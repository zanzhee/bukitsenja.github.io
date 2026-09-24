```mermaid
flowchart TD
    A([Mulai]) --> B[/Terima masukan daya listrik AC 220V dari PLN/]
    B --> C[Konversi AC ke DC 90V via GPU Darat]
    C --> D[Transmisikan daya 90V DC melalui kabel power tether 24 meter]
    D --> E[/Terima tegangan 90V DC pada modul input wahana/]
    E --> F[Distribusikan daya via Konverter Step-Down Ganda<br/>- Jalur 1: Motor 1-2 & FC<br/>- Jalur 2: Motor 3-4, Mini PC, & Aktuator]
    F --> G[/Baca parameter arus dan tegangan real-time via Power Module/]
    G --> H{Apakah Terjadi<br/>Anomali?}
    
    H -- Tidak --> I[Salurkan daya kontinu ke seluruh sistem wahana]
    I -->|Looping pemantauan| G
    
    H -- Ya --> J[Tripping MCB / Aktifkan E-Stop & Putus Jalur Daya Utama]
    J --> K([Selesai / Sistem Berhenti])
