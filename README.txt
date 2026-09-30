WALLET — PWA (menaxhim parash me zë, shqip)
===========================================

STRUKTURA
---------
wallet/
├── index.html                  aplikacioni (i plotë, pa varësi të jashtme)
├── manifest.json               emri, ikonat, ngjyrat, start_url
├── sw.js                       service worker (offline)
├── README.txt                  ky skedar
└── icons/
    ├── icon-192.png
    ├── icon-512.png
    └── icon-512-maskable.png

E RËNDËSISHME: index.html duhet të jetë në RRËNJË të asaj që ngarkon.


1) NETLIFY DROP (më e shpejta, pa llogari)
------------------------------------------
1. Hap https://app.netlify.com/drop
2. Tërhiq dosjen "wallet" (jo .zip-in, jo dosjen prind).
3. Merr URL-në: https://xxxx.netlify.app
4. Opsionale: Site settings → Change site name.


2) GITHUB PAGES
---------------
1. Krijo repo publik, p.sh. "wallet".
2. Ngarko PËRMBAJTJEN e dosjes wallet (jo vetë dosjen), që index.html
   të jetë në rrënjë të repo-s.
3. Settings → Pages → Source: Deploy from a branch → main / (root) → Save.
4. Pas ~1 minutë: https://<user>.github.io/wallet/
   (rrugët janë relative "./", pra nën-dosja funksionon pa ndryshime)


3) PWABUILDER → APK
-------------------
1. Hap https://www.pwabuilder.com
2. Fut URL-në publike → Start.
3. Kontrollon manifest + service worker (duhet të jenë të dy OK).
4. Package For Stores → Android.
   - "Signing key: Create new" për test.
   - Shkarkohet .apk (test) dhe .aab (Play Store).
5. Kopjo .apk në telefon → lejo "Install unknown apps" → instalo.

Pa PWABuilder: hap URL-në në Chrome Android → menu ⋮ → "Install app".
Kjo mjafton për ikonë në ekran + punë offline.


PËRDORIMI
---------
- Herën e parë: vendos buxhetin mujor (ose thuaj "buxheti i muajit tetor 2000 euro").
  Buxheti bartet automatikisht në muajt e ardhshëm.
- Shpenzimet: "shpenzova 2 euro për kafe", "12 euro fastfood dhe 3 euro kafe",
  "dje 45 euro faturën e rrymës", "më 3 tetor 80 euro derivate".
- Të hyra shtesë: "mora 150 euro bonus".
- Pyetje: "sa më ka mbetur?", "sa shpenzova për kafe?".
- Data dhe muaji merren vetë nga ora e telefonit — nuk futen me dorë.
- Raporte: buxhet / shpenzim / kursim, muaj pas muaji, sipas kategorive, eksport CSV.

Zëri punon vetëm mbi HTTPS (Chrome Android). Njohja e zërit përdor "sq-AL";
nëse telefoni nuk e ka shqipen, përdor tastierën ose shto paketën e gjuhës
në: Settings → Google → Search → Voice → Languages.

Të dhënat ruhen vetëm në telefon (localStorage). Pa server, pa llogari.
Backup: Raporte → Eksporto CSV.


PËRDITËSIM I MËVONSHËM
----------------------
Kur ndryshon index.html, ndrysho edhe versionin në sw.js:
    var CACHE = "wallet-v2";
Përndryshe telefoni vazhdon të shfaqë versionin e vjetër nga cache-i.
