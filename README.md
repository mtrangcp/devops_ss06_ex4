## 1. Khởi chạy tiến trình nền với nohup

Cấp quyền thực thi và khởi chạy `loop-monitor.sh` chạy nền:

```bash
chmod +x loop-monitor.sh
nohup ./loop-monitor.sh > /dev/null 2>&1 &
[1] 23456
```

Kiểm tra số định danh tiến trình (PID):

```bash
$ ps aux | grep loop-monitor.sh
user     23456  0.0  0.1  12480  2840 pts/0    S    15:35   0:00 /bin/bash ./loop-monitor.sh
user     23460  0.0  0.0   8900   880 pts/0    S+   15:35   0:00 grep --color=auto loop-monitor.sh
```

---

## 2. Kiểm tra ghi log liên tục

Xem nội dung tệp tin `/tmp/monitor.log`:

```bash
$ tail -n 10 /tmp/monitor.log
System time: Tue Oct  6 15:35:05 UTC 2026
System time: Tue Oct  6 15:35:10 UTC 2026
System time: Tue Oct  6 15:35:15 UTC 2026
System time: Tue Oct  6 15:35:20 UTC 2026
System time: Tue Oct  6 15:35:25 UTC 2026
System time: Tue Oct  6 15:35:30 UTC 2026
System time: Tue Oct  6 15:35:35 UTC 2026
System time: Tue Oct  6 15:35:40 UTC 2026
System time: Tue Oct  6 15:35:45 UTC 2026
System time: Tue Oct  6 15:35:50 UTC 2026
```

---

## 3. Dừng tiến trình bằng tín hiệu Kill

Dừng tiến trình PID `23456` bằng tín hiệu `SIGTERM` (15):

```bash
$ kill -15 23456
```

Kiểm tra lại xem tiến trình đã dừng hoàn toàn chưa:

```bash
$ ps aux | grep loop-monitor.sh
user     23490  0.0  0.0   8900   880 pts/0    S+   15:36   0:00 grep --color=auto loop-monitor.sh
```
