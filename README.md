# Docker Container Run করা

আগে build করা Docker image (`my-app`) থেকে কীভাবে Docker Desktop এর মাধ্যমে container run করতে হয়, container verify করতে হয়, এবং random host port assign করতে হয় — সেটা এই ডকুমেন্টে দেখানো হয়েছে।

---

## ধাপ ১: Docker Desktop থেকে Container Run করা

Docker Desktop open করে **Images** section এ যেতে হবে। সেখানে build করা image (`my-app`) এর পাশে **Run** বাটনে click করতে হবে।

![Docker Desktop Images - Run click](https://imgur.com/1nJVSwS.png)

---

## ধাপ ২: Optional Settings দেওয়া

Run বাটনে click করলে একটা settings panel আসবে, সেখানে:

| Field | কী দিতে হবে |
|---|---|
| **Container name** | container এর জন্য একটা নাম দিতে হবে (না দিলে Docker নিজেই random একটা নাম generate করে দেয়) |
| **Host port** | project এ যে port ব্যবহার করা হয়েছে (এখানে `3000`) সেটা দিতে হবে, অথবা `0` দিলে Docker নিজে থেকে একটা random available port assign করে দেবে |

সব ঠিক থাকলে **Run** বাটনে click করতে হবে।

![Container settings - name and host port](https://imgur.com/O83Xz0Q.png)

---

## ধাপ ৩: Container Verify করা

Run করার পর Docker Desktop এর **Containers** section এ গেলে container টা running state এ show করবে, এবং server এর logs ও দেখা যাবে।

![Container running](https://imgur.com/0pJ4F0J.png)

Container এর সাথে যে port assign করা হয়েছিল, সেই port এ click করলে সরাসরি browser এ app টা open হয়ে যাবে।

![Browser output via port](https://imgur.com/i5yA05X.png)

---

## ধাপ ৪: Host Port: 0 দিয়ে Random Port Assign করা

Host port field এ `0` দিয়ে run করলে Docker নিজে থেকে একটা free/random port বেছে নিয়ে container এর সাথে map করে দেয় — এটা তখন কাজে লাগে যখন নির্দিষ্ট port (যেমন `3000`) আগে থেকেই অন্য কোনো process/container ব্যবহার করছে।

![Host port 0 for random assignment](https://imgur.com/gZtg2vw.png)

Docker যে random port assign করেছে সেটা container এর details এ দেখা যাবে:

![Random port number assigned](https://imgur.com/Cdx0AbC.png)

সেই random port এ click করলেও একইভাবে browser এ app টা open হয়ে যাবে:

![App running on random port](https://imgur.com/TU92wgX.png)

---

> **Note:** Host port হলো আমাদের local machine এর port, আর container এর ভেতরের port (Dockerfile এ যেটা `EXPOSE` করা হয়েছিল) সবসময় same থাকে। Docker এই দুইটার মধ্যে mapping করে দেয় — তাই বাইরে থেকে যেকোনো host port ব্যবহার করলেও ভেতরে app ঠিকমতোই তার নিজের port এ চলে।

---
