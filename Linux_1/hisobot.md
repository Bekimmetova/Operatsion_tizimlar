# PART 1. Ubuntu 20.04 Server LTS o’rnatildi, versiya tekshiruvi:<br>
_cat /etc/issue_ <br>
![terminaldan tasvir](images/1part.png)<br>
# PART 2. User yaratish. (newuser)ni adm guruhiga qo’shish.<br>
_sudo adduser newuser_ <br>
_sudo usermod -aG adm newuser_ <br>
_cat /etc/passwd | grep newuser_ <br>
![terminaldan tasvir](images/2part.png)<br>
# PART 3. OS networkni o’rnatish<br>
_1. Hostname o'zgartirish_ <br>
_sudo hostnamectl set-hostname user-1_ <p>
_2. Timezone sozlash_ <br>
_sudo timedatectl set-timezone Asia/Tashkent_ <p>
_3. Network interfeyslar_ <br>
_ip a      yoki      ip link_ <p>
_4. DHCP orqali IP olish (lo interfeysi bu localhost uchun)_ <br>
_ip a | grep inet_ <p>
_5. Gateway IP aniqlash_ <br>
_ip route | grep default_ <p>
_6. External IP aniqlash (masalan wget yordamida)_ <br>
_curl ifconfig.me_ <p>
![terminaldan tasvir](images/3part1.png)<br>
_7. Netplan orqali statik IP sozlash:_ <br>
_sudo nano /etc/netplan/00-installer-config.yaml_ <br>
_Ichida quyidagidek yoziladi:_ <br>
_(IP va gateway ni o'zingizga moslab belgilang)network:_ <br>
![terminaldan tasvir](images/3part2.png)<br>
![terminaldan tasvir](images/3part3.png)<br>
_ctrl+o keyin enter keyin ctrl+x keyin quyudagi komand=> sudo netplan apply_ <p>
_8. Ping bilan tekshirish_ <br>
_ping -c 4 1.1.1.1_ <br>
_ping -c 4 ya.ru_ <br>
![terminaldan tasvir](images/3part4.png)<br>
# PART 4. Sistemani yangilash kerak, oxirida yana yangilash deganda yangilash yo’q deb chiqishi kerak.<br>
_sudo apt update_ <br>
_sudo apt upgrade -y_ <br>
_sudo apt update_ <br>
![terminaldan tasvir](images/4part.png)<br>
# PART 5. Using the sudo command<br>
_sudo (SuperUser DO) buyrug‘i – oddiy foydalanuvchiga administrator (ya'ni root) huquqlari bilan vaqtincha buyruq bajarish imkonini beradi. Bu xavfsizlik va nazorat uchun muhimdir – foydalanuvchi doimiy root bo‘lishiga hojat yo‘q, lekin kerakli paytda muhim amallarni bajara oladi (masalan, konfiguratsiya fayllarini tahrirlash, xizmatlarni ishga tushirish, paket o‘rnatish va hokazo)._ <br>
_Men newuser foydalanuvchisiga sudo vakolati berdim. sudo buyrug‘i Linux tizimida administrator vakolatlari bilan vaqtinchalik buyruq bajarish imkonini beradi. newuser foydalanuvchisi o’tish orqali tizim nomini user-new ga o‘zgartirdim va bu o‘zgarishlarni hostname komandasi orqali tekshirdim._ <br>
_sudo usermod -aG sudo newuser - >  newuser ga sudo huquqini beradi_ <br>
_sudo passwd newuser - >  newuserga parol o’rnatadi_ <br>
_su – newuser  - >  tizimga newuser sifatida kiradi_ <br>
_sudo hostnamectl set-hostname user-new - > hostname ni_ <br>
_user-new ga o’zgartiradi_ <br>
_hostname - > hostnameni ko’rish_ <br>
_sudo apt update_ <br>
_sudo apt update_ <br>
![terminaldan tasvir](images/5part.png)<br>
# PART 6. Vaqt xizmatlarini o’rnatish va sozlash<br>
_sudo sudo timedatectl set-ntp true   - >  Ubuntu tizimida avtomatik vaqtni sinxronlash uchun systemd-timesyncd yoki chrony kabi xizmatlarni o‘rnatish mumkin. Quyidagi buyruqlar orqali systemd-timesyncd xizmatini faollashtiramiz_ <br>
_timedatectl set-timezone Asia/Tashkent  - >  joriy zonani sozlash_ <br>
_timedatectl show - > vaqtni tekshirish_ <br>
![terminaldan tasvir](images/6part.png)<br>
# PART 7. Matn muharrirlarini o’rnatish va ulardan foydalanish<br>
VIM ning birinchi versiyasi 1991- yil 2 -noyabrda Niderlandiyada Barm Molenar chiqargan.<br>
_**File muharrirlarini o’rnatish**<br>
sudo apt update<br>
sudo apt install vim nano joe -y<p>
**Har bir tahrirlovchida fayl yaratish saqlash:**<br>
**Vimda** - vim test_vim.txt<br>
nikname yoziladi<br>
Esc bosiladi, :wq  yozilib Enter bosiladi.<br>
**Nano** – nano test_nano.txt<br>
nikname yoziladi<br>
Ctrl+O bosiladi va Enter keyin Ctrl+X<br>
**Joe** – joe test_joe.txt<br>
nikname yoziladi<br>
Ctrl+K so’ng Ctrl+X va Enter_ <br>
![terminaldan tasvir](images/7part1.png)<br>
![terminaldan tasvir](images/7part1a.png)<br>
![terminaldan tasvir](images/7part1b.png)<br>
_**matn muharririda o’zgartir lekin saqlamasdan chiqib ket**<br>
**Vim**<br> vim test_vim.txt<br> - > i bosiladi insert rejimga o’tish uchun, <br>
o’zgartiriladi, Esc tugmasi, :q! , keyin Enter_ <br>
![terminaldan tasvir](images/7part2.png)<br>
_**Nano**<br> nano test_nano.txt<br>
o’zgartiramiz, Ctrl+X, N bosiladi._ <br>
![terminaldan tasvir](images/7part3.png)<br>
_**Joe**<br> joe test_joe.txt<br>
o’zgartiramiz, Ctrl+C, keyin y bosiladi._ <br>
![terminaldan tasvir](images/7part4.png)<br>
_**Har bir muharrirda so’zlarni qidirish va almashtirish:<br>
Vim**   vim test_vim.txt<br>
/nickname → Enter<br>
:%s/nickname/user/g  → Enter<br>
:wq → Enter_ <br>
![terminaldan tasvir](images/7part5a.png)<br>
![terminaldan tasvir](images/7part5b.png)<br>
_**Nano**<br>   nano test_nano.txt<br>
Ctrl+W , keyin nickname, keyin Enter<br>
Ctrl+\ , keyin nickname → Enter, user → Enter<br>
Ctrl+o → Enter → Ctrl+X_ <br>
![terminaldan tasvir](images/7part6a.png)<br>
![terminaldan tasvir](images/7part6b.png)<br>
_**Joe**<br>   joe test_joe.txt<br>
Ctrl+K →  Enter → nickname  → R → user → Enter → Y →_ <br>
![terminaldan tasvir](images/7part7a.png)<br>
![terminaldan tasvir](images/7part7b.png)<br>
# PART 8. SSHD xizmatini o’rnatish va asosiy konfiguratsiyasi<br>
_SSHD paketni o’rnatish<br>
sudo apt update<br>
sudo apt install openssh-server -y<p>
xizmatni avtomatik ishga tushurishga sozlash<br>
sudo systemctl enable ssh<br>
sudo systemctl start ssh<p>
portni 2022ga o’zgartirish<br>
sudo sed -i 's/#Port 22/Port 2022/' /etc/ssh/sshd_config<br>
sudo systemctl restart ssh<p>
sshd jarayonini ps bilan tekshirish(ps – jarayonlarni korsatadi; aux – barcha foydalanuvchilar; grep [s]shd – natijada sshd jarayonini ajratib korsatish)<br>
ps aux | grep [s]shd<p>
tizimni qayta yuklash<br>
sudo reboot<p>
agar netstat bolmasa o’rnatish<br>
sudo apt install net-tools -y<p>
netstatdan natijani ko’rsatish<br>
netstat -tan | grep ':2022'_ <br>
![terminaldan tasvir](images/8part.png)<br>
_“-t”: TCP portlar; “-a”: barcha portlar; “-n”: raqamli format (DNSga murojaat yo‘q)._ <br>
# PART 9. top, htop utilitalarini o’rnatish va ishlatish<br>
_sudo apt update<br>sudo apt install htop -y     odatda o’rnatilgan bo’ladi<br>top -n 1     → top ni ishga tushurish_ <br>
![terminaldan tasvir](images/9part1.png)<br>
![terminaldan tasvir](images/9part2.png)
# PART 10. fdisk utilitasidan foydalanish<br>
_sudo fdisk -l<br>
qattiq disk nomi:  /dev/mapper/ubuntu--vg-ubuntu--lv<br>
hajmi(capacity):   23.102 GiB<br>
sektorlar soni:    50323456_ <br>
![terminaldan tasvir](images/10part.png)<br>
# PART 11. df utilitasidan foydalanish disk maydoni haqida ma’lumot olish<br>
_df /<br>
bo’lim hajmi: 24590672<br>
band joy hajmi: 6864696<br>
bo’sh joy hajmi: 16451508<br>
foydalanish foizi: 30%<br>
df -Th/<br>
bo’lim hajmi: 24G<br>
band joy hajmi: 6.6G<br>
bo’sh joy hajmi: 16G<br>
foydalanish foizi: 30%_  <br>
# PART 12. du utilitasidan foydalanish disk maydoni haqida ma’lumot olish<br>
_du /home /var /var/log_<br>
![terminaldan tasvir](images/12part1.png)<br>
_du -h /home /var /var/log_<br>
![terminaldan tasvir](images/12part2.png)<br>
_du -h /var/log/*_<br>
![terminaldan tasvir](images/12part3.png)<br>
# PART 13. ncdu utilitalarini o’rnatish va foydalanish<br>
_ncdu (NCurses Disk Usage) — bu diskdagi fayllar va papkalar qancha joy egallaganini interaktiv tarzda ko‘rsatadigan terminal dasturi. U du (disk usage) buyrug‘ining qulayroq, ko‘rgazmali interfeysga ega versiyasidir.<br>/var/log/dmesg_ <br>
![terminaldan tasvir](images/13parta.png)<br>
![terminaldan tasvir](images/13partb.png)<br>
# PART 14. Tizimli jurnallar bilan ishlash<br>
_sudo systemctl restart ssh<br>
grep 'sshd' /var/log/syslog_ <br>
![terminaldan tasvir](images/14parta.png)<br>
![terminaldan tasvir](images/14partb.png)<br>
# PART 15. CRON rejalashtiruvchisidan foydalanish<br>
_uptime buyrugini har 2 daqiqada ishlatish<br>
(crontab -l 2>/dev/null; echo "*/2 * * * * /usr/bin/uptime >> /var/log/uptime.log") | crontab -<p>
loglardagi CRON ijro chiziqlarini topish<br>
grep CRON /var/log/syslog | tail -n 10_ <br>
![terminaldan tasvir](images/15parta.png)<br>
_joriy CRON vazifalarini ko’rish<br>
crontab -l_<br>
![terminaldan tasvir](images/15partb.png)<br>