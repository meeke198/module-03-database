# module-03-database
[Bài tập] Truy vấn dữ liệu với CSDL Quản lý sinh viên
* Hiển thị tất cả các sinh viên có tên bắt đầu bảng ký tự ‘h’

USE Student_management;
SELECT \*
from Student
where StudentName LIKE 'h%';
* Hiển thị các thông tin lớp học có thời gian bắt đầu vào tháng 12.
USE Student_management;
SELECT \*
from Class
where StartDate >= '2008/12/01 00:00:00' AND StartDate < '2008-12-31 00:00:00';
* Hiển thị tất cả các thông tin môn học có credit trong khoảng từ 3-5.
USE Student_management;
SELECT \*
from Subject
where credit >= 3 AND credit <= 5;
* Thay đổi mã lớp(ClassID) của sinh viên có tên ‘Hung’ là 2.

USE Student_management;
UPDATE Student
SET ClassId = 2
WHERE StudentName = 'Hung';


14:10:00 UPDATE Student SET ClassId = 2 WHERE StudentName = 'Hung' Error Code: 1175. You are using safe update mode and you tried to update a table without a WHERE that uses a KEY column. To disable safe mode, toggle the option in Preferences -> SQL Editor and reconnect. 0.00065 sec


This error message is related to the "safe update mode" in the SQL editor being enabled. It prevents accidental updates to the database without a WHERE clause that uses a key column. To resolve the issue, disable the safe update mode option in the preferences and reconnect to the database.


Disable Safe Update Mode
Go to Edit --> Preferences.
Click "SQL Editor" tab and uncheck "Safe Updates" (rejects UPDATEs and DELETEs with no restrictions) check box.
Query --> Reconnect to Server.


* Hiển thị các thông tin: StudentName, SubName, Mark. Dữ liệu sắp xếp theo điểm thi (mark) giảm dần. nếu trùng sắp theo tên tăng dần.

USE Student_management;
SELECT S.StudentName, Sub.SubName, M.Mark
from Student S
join Mark M on S.StudentId = M.StudentId
join Subject Sub on Sub.SubId = M.SubId
order by Mark DESC, StudentName ASC;


