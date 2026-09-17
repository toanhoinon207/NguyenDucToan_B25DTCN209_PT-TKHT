# Phần 1 - Phân tích thực thể

| Class | Thuộc tính chính | Vai trò |
|---|---|---|
| **Student** | studentId, name, email, phone | Sinh viên |
| **Course** | courseId, name, description | Môn học |
| **Schedule** | scheduleId, date, startTime, endTime, mode | Lịch học |
| **LabRoom** | roomId, name, location, capacity | Phòng lab |
| **Attendance** | attendanceId, scanTime, deviceId, status | Điểm danh QR |
| **StudyGroup** | groupId, name, leaderId, status, createdAt, dissolvedAt | Nhóm học tập + quản lý bài tập nhóm |

# Phần 2 - Thiết kế kiến trúc toàn hệ thống 