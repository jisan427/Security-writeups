
Repeater

Burp Suite Repeater নিয়ে এই লেখা আমি আমার আগের practice experience থেকে লিখছি। এই tool টা আমি web penetration testing শেখার শুরুর দিকেই ভালোভাবে ব্যবহার করেছি। তখন lab solve করতাম আর request response বুঝার চেষ্টা করতাম কিন্তু তখন আলাদা করে writeup লেখা হয়নি। এখন শেখা জিনিসগুলো整理 করার জন্য এই লেখা।

Burp Suite Repeater মূলত একটি manual testing tool। Proxy দিয়ে যেই HTTP request ধরা হয় সেটা Repeater এ পাঠিয়ে বারবার পাঠানো যায়। Request এর parameter change করে server কিভাবে respond করে সেটা দেখা যায়। Automated scan অনেক সময় যেগুলো ধরতে পারে না Repeater দিয়ে সেগুলো manually বোঝা যায়।

আমি সাধারণত Repeater ব্যবহার করতাম access control আর logic related issue test করার জন্য। Parameter change করলে অন্য user এর data আসছে কিনা সেটা দেখা হতো। SQL injection বা XSS এর ক্ষেত্রে payload দিয়ে response observe করা হতো। Authentication বা authorization ঠিকভাবে কাজ করছে কিনা সেটাও Repeater দিয়ে test করা হতো।

Request Repeater এ পাঠানোর সময় প্রথমে Burp Proxy চালু করে application টা normal ভাবে ব্যবহার করতাম। এরপর HTTP history থেকে দরকারি request select করে Repeater এ পাঠাতাম। তারপর request এর ভিতরের parameter নিজের মতো করে পরিবর্তন করে বারবার send করতাম।

একটি common scenario ছিল user id related test। একই request রেখে শুধু id value পরিবর্তন করে response দেখা হতো। যদি অন্য user এর information পাওয়া যেত তাহলে বুঝা যেত access control ঠিকভাবে implement করা হয়নি। এইভাবে অনেক PortSwigger lab আমি solve করেছি।

Repeater দিয়ে manual testing করার সবচেয়ে বড় সুবিধা হলো request এর উপর পুরো control পাওয়া যায়। কোন parameter কিভাবে কাজ করছে সেটা পরিষ্কার বোঝা যায়। Application এর behaviour বুঝতে এই tool টা আমার শেখার সময় অনেক help করেছে।

সবশেষে বলা যায় Burp Suite Repeater আমার web penetration testing শেখার সময় সবচেয়ে বেশি ব্যবহার করা tool গুলোর একটি। তখন লিখে রাখা হয়নি কিন্তু practical experience থেকে এখনো বুঝি manual testing skill develop করতে এই tool খুবই গুরুত্বপূর্ণ।




