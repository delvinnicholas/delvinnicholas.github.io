---
title: "Advent of Cyber 2021 - Day 1 & 2"
date: 2021-12-10T21:17:25+07:00
slug: ""
description: "Write-up for AOC Day 1 & 2 at TryHackMe"
keywords: []
draft: false
tags: [TryHackMe, Web]
math: false
toc: false
---

**Day 1 - Save The Gifts**\
IDOR Vulnerability \
Question : 
- *After finding Santa's account, what is their position in the company?*
Dengan mengubah parameter ID, kita dapat mengakses data milik orang lain.
`The Boss`
- *After finding McStocker's account, what is their position in the company?*
`Build manager`
- *After finding the account responsible for tampering, what is their position in the company?*\
`Mischief Manager`
- *What is the received flag when McSkidy fixes the Inventory Management System?*\
`THM{AOC_IDOR_2B34BHI3}`
---
**Day 2 - Elf HR Problems**\
HTTPS, cookie\
Below is a summary of how cookie values could be manipulated
1. Obtain a cookie value from registering or signing up for an account.
2. Decode the cookie value.
3. Identify the object notation or structure of the cookie.
4. Change the parameters inside the object to a different parameter with a higher privilege level, such as admin or administrator.
5. Re-encode the cookie and insert the cookie into the value space; this can be done by double-clicking the value box.
6. Action the cookie; this can be done by refreshing the page or logging in.

Question : 
- *Open the static site in a new tab, Register an account, and verify the cookies using the Developer Tools in your browser.*
![910e2f94eaf3731de652a15f0728e02d.png](/images/aocday1/910e2f94eaf3731de652a15f0728e02d.png)
- *What is the name of the new cookie that was created for your account?
`user-auth` 
![5e1dc8de25e1b6473775c77de1c946e4.png](/images/aocday1/5e1dc8de25e1b6473775c77de1c946e4.png)

- *What encoding type was used for the cookie value?*\
`hexadecimal`
- *What object format is the data of the cookie stored in?*\
`JSON`
- *Manipulate the cookie and bypass the login portal. What is the value of the administrator cookie? (username = admin)*
Ambil value dari cookie yang kita punya, kemudian kita decode menggunakan hexadecimal, dan kita ganti value username menjadi 'admin'. Ubah kembali menjadi hexadecimal dan ubah value cookie yang kita punya dengan cookie baru. 
![75531db4e0294589ee4428d4d35d68fa.png](/images/aocday1/75531db4e0294589ee4428d4d35d68fa.png)
![501575c0478b451b8bf1c46830e0e248.png](/images/aocday1/501575c0478b451b8bf1c46830e0e248.png)\
`7b636f6d70616e793a2022546865204265737420466573746976616c20436f6d70616e7922
2c206973726567697374657265643a2254727565222c20757365726e616d653a2261646d696e227d`
Setelah disimpan, halaman di-refresh dan kita masuk menjadi admin
![d9edfafc1f3a25589f99904dd661d724.png](/images/aocday1/d9edfafc1f3a25589f99904dd661d724.png)
- *What team environment is not responding?*\
`HR`
- *What team environment has a network warning?*\
`Application`