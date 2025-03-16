# MR.Hidden's Process Execution Simulator

این پروژه یک شبیه‌ساز اجرای فرآیند است که الگوریتم‌های زمان‌بندی مختلف پردازنده را پیاده‌سازی می‌کند. هدف این پروژه ارائه ابزاری برای درک و مقایسه عملکرد الگوریتم‌های زمان‌بندی مختلف است.

## ویژگی‌ها

* پیاده‌سازی الگوریتم‌های زمان‌بندی زیر:
    * First-Come, First-Served (FCFS)
    * Shortest-Job-First (SJF)
    * Shortest-Remaining-Time (SRT)
    * Round-Robin (RR)
    * Multi-Level Feedback Queue (MLFQ)
    * Multi-CPU (MCPU)
* محاسبه زمان انتظار، زمان سرویس و زمان بازگشت برای هر فرآیند.
* نمایش نتایج به صورت جدول.
* قابلیت تنظیم تعداد CPU ها در الگوریتم MCPU
* قابلیت تنظیم کوانتوم زمان در الگوریتم RR
* قابلیت ریست کردن اطلاعات فرآیند ها.

## پیش‌نیازها

* Python 3.x

## نحوه استفاده

1.  فایل `Excute.py` و `Process_Model.py` را در یک پوشه قرار دهید.
2.  یک لیست از فرآیندها را ایجاد کنید. هر فرآیند باید یک دیکشنری با کلیدهای زیر باشد:
    * `ProcessID`: شناسه فرآیند (عدد صحیح).
    * `ProcessArriveTime`: زمان ورود فرآیند (عدد صحیح).
    * `ProcessServiceTime`: زمان سرویس فرآیند (عدد صحیح).
3.  یک شیء از کلاس `Excute` ایجاد کنید و لیست فرآیندها را به عنوان آرگومان به سازنده ارسال کنید.
4.  متد `calculate_` را برای الگوریتم زمان‌بندی مورد نظر فراخوانی کنید.
5.  متد `show_process` را برای نمایش نتایج فراخوانی کنید.

### مثال

```python
from Process_Model import Process
from Excute import Excute

process_list = [
    Process(1, 0, 5),
    Process(2, 1, 3),
    Process(3, 2, 8),
    Process(4, 3, 6),
]

executor = Excute(process_list)

# calculate FCFS
executor.calculate_FCFS

# show results
executor.show_process()

# reset data
executor.reset

# calculate RR with quantum time 2 and context switch time 1
executor.qtime = 2
executor.cn_switch = 1
executor.calculate_RR
executor.show_process()

#calculate MCPU with 2 cpu
executor.c_cpu = 2
executor.calculate_MCPU
executor.show_process()

#calculate MLFQ
executor.calculate_MLFQ
executor.show_process()
