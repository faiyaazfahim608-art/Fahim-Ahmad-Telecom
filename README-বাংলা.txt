FN Telecom PWA ফাইল

১) এই ZIP-এর manifest.json, service-worker.js এবং icons ফোল্ডারটি আপনার GitHub repository-র index.html ফাইলের একই মূল (root) জায়গায় আপলোড করুন।
২) index.html-এর <head> অংশে যোগ করুন:
<link rel="manifest" href="./manifest.json">
<meta name="theme-color" content="#087b4e">
৩) <body>-এর শুরুতে header-এর ভেতরে Install বাটন চাইলে যোগ করুন:
<button id="installAppBtn" class="hidden" style="margin-top:12px;background:#fff;color:#087b4e">📲 অ্যাপ ইনস্টল করুন</button>
৪) </body>-এর ঠিক আগে এই script যোগ করুন:
<script>
let deferredInstallPrompt = null;
const installBtn = document.getElementById("installAppBtn");
window.addEventListener("beforeinstallprompt", (event) => {
  event.preventDefault();
  deferredInstallPrompt = event;
  if (installBtn) installBtn.classList.remove("hidden");
});
if (installBtn) {
  installBtn.addEventListener("click", async () => {
    if (!deferredInstallPrompt) {
      alert("Chrome-এর মেনু থেকে 'Install app' অথবা 'Add to Home screen' নির্বাচন করুন।");
      return;
    }
    deferredInstallPrompt.prompt();
    await deferredInstallPrompt.userChoice;
    deferredInstallPrompt = null;
    installBtn.classList.add("hidden");
  });
}
window.addEventListener("appinstalled", () => {
  if (installBtn) installBtn.classList.add("hidden");
});
if ("serviceWorker" in navigator) {
  window.addEventListener("load", () => {
    navigator.serviceWorker.register("./service-worker.js")
      .catch(err => console.error("Service Worker registration failed:", err));
  });
}
</script>

গুরুত্বপূর্ণ:
- GitHub Pages-এ HTTPS চালু থাকতে হবে (আপনার Pages লিংকে HTTPS আছে)।
- index.html, manifest.json, service-worker.js একই root folder-এ থাকতে হবে।
- আইকন দুটি icons ফোল্ডারের ভেতরে থাকতে হবে।
- প্রথমবার আপলোডের পর Chrome-এ সাইট খুলে কিছুক্ষণ অপেক্ষা করুন; তারপর Install বাটন/Chrome menu থেকে install করুন।
- ইনস্টল হওয়া অ্যাপের Firebase/অর্ডার ফিচার চালাতে ইন্টারনেট প্রয়োজন। Service worker কেবল অ্যাপের মূল পেজ/আইকন ক্যাশ করে।
