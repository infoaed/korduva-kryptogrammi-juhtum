# korduva-kryptogrammi-juhtum

Mis juhtus e-häälte auditeerimisel 2025. aasta KOV valimistel?

Audiitori 20.10.2025 toimingu käigus leidis aset segadus, mille asjaolud vaikib audiitor maha ka [oma 22.12.2025 lõpparuandes](https://www.valimised.ee/sites/default/files/2025-12/L%C3%B5pparuanne%20KOV2025%20e-h%C3%A4%C3%A4letuse%20audit%2022.12%201.asice).

Esialgse kokkuvõtte toimunust leiab [3.11.2025 blogipostitusest](https://gafgaf.infoaed.ee/posts/korduva-kryptogrammi-juhtum/), mille kohta on ka [kokkuvõttev video](https://youtu.be/clmqgo9b6dY).

Kui tahad ise sammud läbi teha, siis:

```
rm -r out-*
rm -r log

./processor checkAndSquash --conf certs.asice --params processor.asice

digidoc-tool create --file=out-2/KOV_2025-bb-2.json.sha256sum out-2/KOV_2025-bb-2.json.sha256sum.asice

./processor revokeAndAnonymize --conf certs.asice --params processor.asice

./auditor integrity --conf certs.asice --params auditor.asice
```
