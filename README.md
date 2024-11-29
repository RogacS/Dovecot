# Dovecot
Dovecot ir populāra IMAP un POP3 pasta servera programmatūra, kas pazīstama ar savu veiktspēju, drošību un vienkāršu iestatīšanu.

## Sistēmas prasības

### Operētājsistēmas
Dovecot darbojas uz dažādām Unix līdzīgām operētājsistēmām, tostarp Linux (Ubuntu, Debian, u.c.), FreeBSD, OpenBSD un macOS.

### Procesors
Minimālā prasība ir Pentium III vai līdzvērtīgs, savukārt lielai lietotāju slodzei ieteicams moderns daudzseržu procesors.

### Atmiņa (RAM)
Minimālais RAM apjoms ir 512 MB, bet ieteicamais - 2 GB vai vairāk; ja sistēmā ir daudz lietotāju vai tiek veiktas intensīvas datu apstrādes darbības.

---

## Instalācija

1. Pirms Dovecot instalēšanas ieteicams atjaunināt sistēmu, lai aktualizētu visus paketēs, izmantojot komandu:
```bash
sudo apt update && sudo apt upgrade.
```

3. Lai uzstādītu Dovecot serverī Ubuntu vai Debian, izpildiet komandu:
sudo apt install dovecot-core dovecot-imapd dovecot-pop3d

4. Pēc instalēšanas ir nepieciešams konfigurēt Dovecot, mainot konfigurāciju failā /etc/dovecot/dovecot.conf.
Lai rediģētu failu, atveriet to, izmantojot komandu: 
sudo nano /etc/dovecot/dovecot.conf.

  Šajā posmā pietiek pārliecināties, ka rindiņas ar IMAP un/vai POP3 protokola iestatījumiem ir atkomentētas un norādīts: 
protocols = imap pop3

4. Tālāk konfigurējiet mailboxes un iespējot SSL/TLS:
sudo nano /etc/dovecot/conf.d/10-mail.conf
sudo nano /etc/dovecot/conf.d/10-ssl.conf

  Failā 10-mail.conf iestatīt pasta atrašanās vietu:
mail_location = maildir:~/Maildir

  Failā 10-ssl.conf ieslēdziet SSL un norādiet ceļu uz jūsu sertifikātiem:
ssl = required
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_key = </etc/ssl/private/dovecot.key

  Ja jums nav SSL sertifikāta, jūs varat izveidot pašparakstītu sertifikātu, izmantojot komandu:
sudo openssl req -new -x509 -days 365 -nodes -out /etc/ssl/certs/dovecot.pem -keyout /etc/ssl/private/dovecot.key

5. Tagad ir iespējams palaist Dovecot, izmantojot komandu:
sudo systemctl start dovecot










