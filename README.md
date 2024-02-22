# Tema 3 - Implementarea Protocolului BitTorrent

## Student: Gîrniță Alexandra-Claudia
## Grupa: 332CC

### Descriere
Acest proiect simulează transferul de date folosind protocolul BitTorrent, evidențiind aspectele fundamentale ale partajării de fișiere într-un mediu distribuit. Proiectul modelează interacțiunea dintre clienți și tracker, gestionarea swarm-urilor, descărcarea și încărcarea segmentelor de fișiere între peer-uri.

### Structuri de Date Principale
- `FileData`: Stochează informațiile despre un fișier, inclusiv numele, segmentele, și swarm-ul de clienți.
- `Segment`: Reprezintă un segment al fișierului, conținând hash-ul și un flag de posesie.
- `SwarmUnit`: Conține informații despre un seed/peer, inclusiv rank-ul și un array cu flaguri pentru segmentele deținute.

### Funcționare
1. **Inițializarea Clienților**: Fiecare client este inițializat cu datele fișierelor pe care le deține și începe comunicarea cu tracker-ul prin intermediul unui thread de download.
2. **Download**: Clienții solicită segmente lipsă de la peer-uri selectate aleatoriu și actualizează periodic tracker-ul cu progresul lor.
3. **Update**: După descărcarea unui număr de segmente, clienții actualizează tracker-ul cu starea lor curentă folosind `send_data_to_tracker`.
4. **Finalizarea Transferului**: Când toate fișierele sunt descărcate, clienții notifică tracker-ul și încheie procesul.
