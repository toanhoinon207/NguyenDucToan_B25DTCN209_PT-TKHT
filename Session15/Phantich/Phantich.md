# Phần 1 - Đề xuất 2 giải pháp

## Giải pháp 1 - Bảng giá theo tổ hợp điều kiện

### Các Entity

#### SHOWTIME

| Attribute | Data Type | Key |
|---|---|---|
| ShowtimeID | INT | PK |
| MovieID | INT | FK |
| HallID | INT | FK |
| StartTime | DATETIME |  |
| EndTime | DATETIME |  |

#### SEAT

| Attribute | Data Type | Key |
|---|---|---|
| SeatID | INT | PK |
| SeatType | VARCHAR(20) | |

#### TIME_SLOT

| Attribute | Data Type | Key |
|---|---|---|
| TimeSlotID | INT | PK |
| SlotName | VARCHAR(50) | |
| StartTime | TIME | |
| EndTime | TIME | |

#### DAY_TYPE

| Attribute | Data Type | Key |
|---|---|---|
| DayTypeID | INT | PK |
| DayTypeName | VARCHAR(30) | |

#### SPECIAL_DATE

| Attribute | Data Type | Key |
|---|---|---|
| SpecialDateID | INT | PK |
| SpecialDate | DATE | |
| DayTypeID | INT | FK |
| Description | VARCHAR(100) | |

#### TICKET_PRICE

| Attribute | Data Type | Key |
|---|---|---|
| PriceID | INT | PK |
| TimeSlotID | INT | FK |
| DayTypeID | INT | FK |
| SeatType | VARCHAR(20) |  |
| Price | DECIMAL(10, 2) | |
| EffectiveFrom | DATE | |
| EffectiveTo | DATE | |

## Giải pháp 2 - Lưu cấu hình giá dạng JSON

### PRICING_CONFIG

| Attribute | Data Type | Key |
|---|---|---|
| PricingConfigID | INT | PK |
| ConfigName | VARCHAR(100) | |
| ConfigData | JSON | |
| EffectiveFrom | DATE | |
| EffectiveTo | DATE | |

`ConfigData` có thể chứa:

```json
{
  "Standard": {
    "Before17": {
      "Weekday": 70000,
      "Weekend": 80000,
      "Holiday": 100000
    },
    "After17": {
      "Weekday": 90000,
      "Weekend": 100000,
      "Holiday": 120000
    }
  },
  "VIP": {
    "Before17": {
      "Weekday": 90000,
      "Weekend": 100000,
      "Holiday": 120000
    }
  }
}
```

# Phần 2 - So sánh Trade-off

| Tiêu chí | Giải pháp 1: Bảng TICKET_PRICE | Giải pháp 2: JSON |
|---|---|---|
| **Linh hoạt khi Marketing đổi giá** | Cao, chỉ cần thêm/sửa bản ghi | Cao, sửa cấu hình JSON |
| **Tốc độ query** | Nhanh, có thể dùng Index và JOIN | Có thể nhanh với cấu hình nhỏ nhưng truy vấn JSON phức tạp hơn |
| **Xử lý ngày lễ** | Rõ ràng, SPECIAL_DATE -> DAY_TYPE | Vẫn xử lý được nhưng phải kết hợp JSON với ngày đặc biệt |
| **Dễ kiểm tra dữ liệu** | Dễ, mỗi mức giá là một dòng | Khó hơn vì dữ liệu nằm trong JSON |
| **Ràng buộc dữ liệu** | Tốt, dùng PK/FK/UNIQUE | Khó kiểm soát bằng FK |
| **Mở rộng thêm loại ghế/khung giờ** | Thêm dữ liệu | Sửa JSON |
| **Phù hợp CSDL quan hệ** | Rất phù hợp | Kém phù hợp hơn |

# Phần 3 - Triển khai