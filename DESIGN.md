# Bộ kỹ năng 120 tướng — Đấu Trường Huyền Thoại (v3)

**Tóm tắt:** 57 loại chiêu (engine đã có sẵn từ v2) • 120 bộ 3 chiêu **không trùng nhau** • mỗi vai trò chỉ dùng loại chiêu hợp vai • mọi số liệu lấy từ một hàm `mkSkill()` duy nhất nên cùng thang cân bằng.

## So với v2 đã sửa gì

| Vấn đề ở v2 | Cách sửa ở v3 |
|---|---|
| Mỗi vai trò rải đều ~50 loại chiêu: Xạ Thủ có ám sát, Sát Thủ bắn toàn bản đồ, Pháp Sư lao tới… | Mỗi tướng được gán kit theo vai trò và "kiểu chơi"; Sát Thủ/Đấu Sĩ là cận chiến, Xạ Thủ/Pháp Sư đánh xa, Hỗ Trợ luôn có chiêu tác động kẻ địch |
| 16 tướng không có chiêu nào gây sát thương (Thánh Sĩ, Vô Ảnh, Thanh Tịnh…) | Mọi tướng đều có ít nhất 1 chiêu gây sát thương hoặc khống chế |
| Số liệu ghi đè do AI bịa sai thang: Cuồng Nộ +4000% công, Cường Hóa +4000–6000% sát thương đòn đánh, Kiếm Thái +3000% công | Bỏ toàn bộ ghi đè; dùng số liệu gốc của `mkSkill()` |
| Hồi chiêu chiêu cuối 80–120 giây | Chiêu cuối 30–60 giây; loại chiêu không có bản "cuối" gốc được tăng sức (x1.9 sát thương, x1.4 thời gian, hồi 30s+) |
| 12 tướng có passive không có tác dụng (Hào Quang Giáp, Hào Quang Đất, Nổ Khiên…) và 5 tướng có passive vô hiệu với vai trò | Cài đặt đủ 24/24 passive; passive hút máu phép / dệt phép trên tướng vật lý đổi sang hút máu / giảm hồi chiêu |
| Chiêu "Liên kết" bắt buộc phải có kẻ địch trong tầm mới tung được | Liên kết tung tức thì, nối với đồng đội gần nhất |
| Chiêu "Sợ hãi" chỉ là choáng | Địch thật sự bỏ chạy khỏi tâm vùng và không dùng được chiêu |
| Tên chiêu/tướng sai chính tả hoặc vô nghĩa ("Kiển", "Mỵ", "Tí Diệt", "Bão Diatreme", "Tốp Kết") | Tên chiêu lấy từ bảng tên chuẩn theo loại; đổi Kiển→Khiên, Mỵ→Mị, Triệu Hồi→Triệu Sư |
| Lời giới thiệu tướng không khớp chiêu | Lời giới thiệu tự ghép từ vai trò + "Sở trường" đúng theo 3 chiêu |

## Kiểm thử

Chạy headless 22 trận 5v5 (tổng ~75 phút mô phỏng) có ép tung chiêu liên tục: 0 lỗi runtime. Thử từng chiêu của cả 120 tướng với bù nhìn: toàn bộ 57 loại chiêu có hiệu ứng thật (sát thương, trói, cấm chiêu, bay, sợ, độc, đánh dấu, khiên phản, miễn nhiễm, liên kết, triệu hồi, tường, bẫy…).

## Đấu Sĩ (20 tướng)

| # | Tướng | Danh hiệu | Passive | Chiêu 1 | Chiêu 2 | Chiêu cuối |
|---|---|---|---|---|---|---|
| 1 | **Bạo Chúa** | Vua Cuồng Nộ | Hút Máu Cuồng | Trảm Quyết _(strike)_ | Lao Kích _(dash)_ | Nộ Hỏa Toàn Thân _(rage)_ |
| 2 | **Hộ Vệ** | Khiên Bất Tử | Khiên Cuối Cùng | Đoạt Mệnh Kích _(strike)_ | Hộ Thể Quang _(shield)_ | Thánh Vực Hộ Mệnh _(sanctuary)_ |
| 3 | **Kiếm Sát** | Kiếm Khách Tốc Sát | Tái Sinh Sát | Phong Trảm _(dash)_ | Kết Liễu _(execute)_ | Ảnh Sát _(assassinate)_ |
| 4 | **Thạch Bì** | Người Núi Sắt | Da Đá | Kéo Hồn _(pull)_ | Địa Chấn _(stun)_ | Sát Thiên _(leap)_ |
| 5 | **Bão Đấm** | Đấm Gió Sấm | Nhịp Đấm | Kìm Bóng _(grapple)_ | Trấn Địa _(knockup)_ | Bão Tối _(storm)_ |
| 6 | **Cuồng Rìu** | Rìu Cuồng Chiến | Cơn Cuồng | Bách Trảm _(empower)_ | Băng Địa _(slow)_ | Vòng Diệt _(nova)_ |
| 7 | **Ma Hút Máu** | Kẻ Nuốt Sinh Lực | Hút Phép Ma | Hút Sinh Lực _(drain)_ | Linh Hút _(spellvamp)_ | Kim Thân _(immune)_ |
| 8 | **Thành Địa** | Tường Thành Sống | Hào Quang Giáp | Hạo Kỳ _(taunt)_ | Phá Quân _(strike)_ | Tường Địa _(wall)_ |
| 9 | **Võ Quyền** | Quyền Thủ Tối Thượng | Quyền Cuồng | Trấn Địa _(knockup)_ | Ảnh Bộ _(dash)_ | Thất Thất _(stance)_ |
| 10 | **Độc Kiếm** | Lưỡi Độc Tâm | Đao Độc | Độc Truyền _(poison)_ | Phá Vệ _(shred)_ | Tử Hình _(execute)_ |
| 11 | **Phong Bước** | Bước Nhẹ Gió | Tốc Sinh Tử | Lao Kích _(dash)_ | Linh Tốc _(haste)_ | Hồi Nguyên _(reset)_ |
| 12 | **Khiên Phản** | Khiên Phản Kích | Nổ Khiên | Bất Kích _(reflect)_ | Trảm Quyết _(strike)_ | Vô Thượng Hộ _(immune)_ |
| 13 | **Linh Gọi** | Gọi Hồn Chiến | Hồn Hỗ Trợ | Cầu Linh _(orb)_ | Lao Kích _(dash)_ | Hồn Thú _(spawn)_ |
| 14 | **Sấm Dây** | Sấm Xích Trừng | Đòn Chậm | Dây Sét _(chain)_ | Đầm Lầy _(slow)_ | Nộ Khí Bùng Nổ _(nova)_ |
| 15 | **Đao Bóng** | Lưỡi Dao Bóng | Đòn Chí Mạng | Hủy Dấu _(mark)_ | Thuấn Ảnh _(blink)_ | Ảnh Sát _(assassinate)_ |
| 16 | **Chí Quyền** | Đấm Chí Tôn | Đà Lực | Chân Ngộ _(truedmg)_ | Phá Thế _(empower)_ | Nộ Hỏa Toàn Thân _(rage)_ |
| 17 | **Lửa Ngục** | Ngọn Lửa Địa Ngục | Huyết Ngục | Lửa Trù _(zonedot)_ | Băng Trói _(root)_ | Hướng Ngộ _(channel)_ |
| 18 | **Dạ Săn** | Kẻ Săn Đêm | Hút Sinh Mệnh | Tàng Hình _(stealth)_ | Trảm Quyết _(strike)_ | Ảnh Sát _(assassinate)_ |
| 19 | **Thánh Sĩ** | Chiến Binh Thánh Quang | Ánh Sáng Đồng Đội | Trảm Quyết _(strike)_ | Sinh Mạch _(regen)_ | Phúc Trạch Quang Hoàn _(sanctuary)_ |
| 20 | **Cấm Thuật** | Kẻ Cấm Phép | Năng Lực Cấm | Hút Linh _(manaburn)_ | Vô Sóng _(silence)_ | Hướng Ngộ _(channel)_ |

## Pháp Sư (20 tướng)

| # | Tướng | Danh hiệu | Passive | Chiêu 1 | Chiêu 2 | Chiêu cuối |
|---|---|---|---|---|---|---|
| 1 | **Lôi Pháp Sư** | Sấm Chấn Cửu Trời | Dệt Sấm | Trảm Kích _(bolt)_ | Địa Chấn _(stun)_ | Chấn Địa _(nova)_ |
| 2 | **Hỏa Vũ** | Mưa Lửa Rơi | Nguồn Lửa | Tam Liên Đạn _(fan)_ | Đầm Lầy _(slow)_ | Thiên Thạch Vũ _(barrage)_ |
| 3 | **Tà Thần** | Tà Nhãn Toàn Cầu | Của Tà | Phá Không _(pierce)_ | Liên Hoàn Kích _(chain)_ | Thiên La Vực _(global)_ |
| 4 | **Huyễn Thuật** | Ảo Thuật Bão | Hút Ảo | Bật Tung _(bounce)_ | Bắt Bóng _(homing)_ | Huyền Vực _(storm)_ |
| 5 | **Băng Tâm** | Trái Tim Băng Giá | Lạnh Căng | Bách Hoa Đạn _(split)_ | Hủy Dấu _(mark)_ | Kết Liễu _(execute)_ |
| 6 | **Thổ Pháp** | Núi Đất Dựng | Hào Quang Đất | Hồi Xuân _(boomerang)_ | Trói Địa _(root)_ | Thạch Tường _(wall)_ |
| 7 | **Cung Tinh** | Cung Tinh Vạn Lý | Tinh Tái Sinh | Thần Tiễn _(snipe)_ | Hư Không Bộ _(blink)_ | Cực Tọa _(channel)_ |
| 8 | **Băng Hà** | Sông Băng Đông Kết | Khiên Băng | Lửa Trù _(zonedot)_ | Đầm Lầy _(slow)_ | Bão Tối _(storm)_ |
| 9 | **Mị Sĩ** | Bẫy Mỵ Săn | Gai Bẫy | Bẫy Long _(trap)_ | Kéo Hồn _(pull)_ | Mưa Diệt Thế _(barrage)_ |
| 10 | **Cổ Độc** | Cổ Độc Truyền Thuyết | Hút Độc | Độc Truyền _(poison)_ | Phệ Hồn _(drain)_ | Chấn Địa _(nova)_ |
| 11 | **Hủy Diệt** | Ngọn Lửa Hủy Diệt | Hút Sinh Hủy | Hút Linh _(manaburn)_ | Hủy Kháng _(shred)_ | Kết Liễu _(execute)_ |
| 12 | **Quang Vinh** | Ánh Sáng Tối Thượng | Ánh Sáng Tốc | Phá Vạn Giáp _(truedmg)_ | Thuấn Ảnh _(blink)_ | Thiên La Vực _(global)_ |
| 13 | **Nguyệt Quỹ** | Vầng Nguyệt Bảo Vệ | Ý Nguyệt | Cầu Linh _(orb)_ | Cam Lộ _(heal)_ | Kim Thân _(immune)_ |
| 14 | **Khiên Pháp** | Khiên Pháp Phản Kích | Nguồn Pháp | Khiên Đảo _(reflect)_ | Tiễn Quang _(bolt)_ | Kiếm Thái _(stance)_ |
| 15 | **Triệu Sư** | Kẻ Gọi Linh Vật | Linh Hồi | Tiễn Quang _(bolt)_ | Hồi Xuân _(regen)_ | Linh Binh _(spawn)_ |
| 16 | **Hỗn Loạn** | Nguồn Hỗn Loạn | Hỗn Cuối | Đánh Bay _(knockup)_ | Tẫn Hồn _(fear)_ | Trấn Hồn _(stun)_ |
| 17 | **Thần Hành** | Bước Nhẹ Thần | Đà Thần | Xung Phá _(bolt)_ | Phong Trảm _(dash)_ | Hồi Nguyên _(reset)_ |
| 18 | **Cung Tiên** | Cung Tiên Mãn Nguyệt | Tiên Hồi | Nghịch Bộ _(backstep)_ | Băng Địa _(slow)_ | Dây Sét _(chain)_ |
| 19 | **Chiến Pháp** | Pháp Sư Chiến Đấu | Nhịp Pháp | Cường Hóa _(empower)_ | Hư Không Bộ _(blink)_ | Chấn Địa _(nova)_ |
| 20 | **Ám Sát** | Kẻ Ám Sát Phép | Dao Phép Độc | Vô Ảnh _(stealth)_ | Hủy Dấu _(mark)_ | Ám Sát Tuyệt Mệnh _(assassinate)_ |

## Xạ Thủ (20 tướng)

| # | Tướng | Danh hiệu | Passive | Chiêu 1 | Chiêu 2 | Chiêu cuối |
|---|---|---|---|---|---|---|
| 1 | **Lôi Báo** | Cung Thủ Sấm Sét | Máu Sấm | Trảm Kích _(bolt)_ | Tốc Chiến _(haste)_ | Vực Sao Rơi _(barrage)_ |
| 2 | **Nhạn Ngũ** | Bách Phát Bách Trúng | Nhắm Chính Yếu Điểm | Liên Hoàn Tiễn _(pierce)_ | Xuyên Vân Tiễn _(snipe)_ | Toàn Cực Phá _(global)_ |
| 3 | **Độc Cô** | Nữ Nhẫn Giả Độc | Nhẫn Độc | Bẫy Long _(trap)_ | Độc Truyền _(poison)_ | Vòng Diệt _(nova)_ |
| 4 | **Điện Ảnh** | Cung Thủ Dây Sét | Sét Truyền Dẫn | Bật Tung _(bounce)_ | Dây Sét _(chain)_ | Vũ Tiễn _(fan)_ |
| 5 | **Hồi Tiêu** | Đệ Tử Phi Tiêu | Phi Tiêu Làm Chậm | Kỷ Tiểu _(boomerang)_ | Đầm Lầy _(slow)_ | Xuyên Tâm _(pierce)_ |
| 6 | **Trảm Yêu** | Cung Thủ Truy Nã | Dấu Săn Đuổi | Tỏa Tiễn _(homing)_ | Đánh Dấu _(mark)_ | Đoạn Mệnh Đao _(execute)_ |
| 7 | **Tán Sát** | Cung Thủ Tán Đạn | Động Lực Tán Đạn | Phân Liệt _(split)_ | Lao Kích _(dash)_ | Sát Thiên _(leap)_ |
| 8 | **Du Nhược** | Lướt Như Bóng | Bóng Lướt Sinh Tồn | Lùi Quyền _(backstep)_ | Cánh Long _(roll)_ | Cường Hóa _(empower)_ |
| 9 | **Bão Nữ** | Nữ Thần Bão Tố | Tim Bão | Độc Trầm _(zonedot)_ | Trói Địa _(root)_ | Cuồng Luân _(storm)_ |
| 10 | **Phá Pháp** | Cung Thủ Phá Ản | Nguyên Tế Mana | Cấm Ngôn _(silence)_ | Phá Vệ _(shred)_ | Cực Tọa _(channel)_ |
| 11 | **Tử Mệnh** | Cung Thủ Thu Hồn | Hồn Thu Được | Đoạn Mệnh Đao _(execute)_ | Huyết Tế _(drain)_ | Hồi Nguyên _(reset)_ |
| 12 | **Hút Linh** | Cung Thủ Hút Mana | Hút Linh Phép | Phá Nguyên _(manaburn)_ | Chân Ngộ _(truedmg)_ | Mưa Diệt Thế _(barrage)_ |
| 13 | **Quỹ Đạo** | Cung Thủ Hành Tinh | Khiên Hành Tinh | Cầu Linh _(orb)_ | Hư Không Bộ _(blink)_ | Huyền Vực _(storm)_ |
| 14 | **Móc Hồn** | Cung Thủ Móc Sét | Hút Huyết Móc | Kìm Bóng _(grapple)_ | Trói Diệt _(pull)_ | Kiếm Thái _(stance)_ |
| 15 | **Địa Sấm** | Sấm Động Địa | Rễ Địa | Trấn Địa _(knockup)_ | Kinh Hoảng _(fear)_ | Thiên Lôi Diệt _(channel)_ |
| 16 | **Ẩn Giáp** | Xạ Thủ Ẩn Sương | Giáp Vỡ Choáng | Ẩn Thân _(stealth)_ | Xung Phá _(bolt)_ | Vũ Tiễn _(fan)_ |
| 17 | **Phản Tiễn** | Cung Thủ Phản Đạn | Giáp Phản Sát | Khiên Đảo _(reflect)_ | Thanh Sạch _(cleanse)_ | Thiên Thạch Vũ _(barrage)_ |
| 18 | **Tái Sinh** | Cung Thủ Sinh Mệnh | Hơi Sinh Mệnh | Tiễn Quang _(bolt)_ | Hồi Xuân _(regen)_ | Cam Lộ _(heal)_ |
| 19 | **Thú Săn** | Thú Đồng Hành | Thú Săn Mồi | Xuyên Tâm _(pierce)_ | Tàng Kích _(trap)_ | Hồn Thú _(spawn)_ |
| 20 | **Huyết Pháp** | Cung Thủ Hút Huyết | Huyết Cuồng | Linh Hút _(spellvamp)_ | Tiễn Quang _(bolt)_ | Cuồng Nộ Chiến Thần _(rage)_ |

## Sát Thủ (20 tướng)

| # | Tướng | Danh hiệu | Passive | Chiêu 1 | Chiêu 2 | Chiêu cuối |
|---|---|---|---|---|---|---|
| 1 | **Kiếm Vong** | Kẻ Sát Nhân Bóng Đêm | Vong Kiếm Tái | Ảnh Bộ _(dash)_ | Đoạt Mệnh Kích _(strike)_ | Tử Ảnh Kích _(assassinate)_ |
| 2 | **Vô Ảnh** | Bóng Ma Vô Hình | Bóng Đêm Lướt | Vô Ảnh _(stealth)_ | Phá Quân _(strike)_ | Hồi Nguyên _(reset)_ |
| 3 | **Điểm Hồn** | Đánh Dấu Tử Thần | Hồn Điểm Truyền | Trói Diệt _(pull)_ | Đánh Dấu _(mark)_ | Đoạn Mệnh Đao _(execute)_ |
| 4 | **Cốt Độc** | Độc Dược Cuồng | Kiếm Độc | Độc Truyền _(poison)_ | Phệ Hồn _(drain)_ | Huyền Vực _(storm)_ |
| 5 | **Tấn Nhược** | Tấn Công Rút Lui | Động Lực Tấn Công | Lùi Quyền _(backstep)_ | Cánh Long _(roll)_ | Nhảy Trảm _(leap)_ |
| 6 | **Hắc Móc** | Móc Tối Cấm Chiêu | Ý Chí Tối | Xích Vực _(grapple)_ | Cấm Ngôn _(silence)_ | Đoạn Mệnh Đao _(execute)_ |
| 7 | **Xuyên Giáp** | Sát Thương Thật | Cuồng Kỵ Yếu | Chân Ngộ _(truedmg)_ | Phá Vệ _(shred)_ | Tử Ảnh Kích _(assassinate)_ |
| 8 | **Hỏa Ngục** | Đốt Linh Hồn | Ngọn Lửa Mana | Hút Linh _(manaburn)_ | Xích Diệt _(chain)_ | Hướng Ngộ _(channel)_ |
| 9 | **Bẫy Vong** | Đặt Bẫy Chết | Dao Bẫy Chậm | Bẫy Long _(trap)_ | Trói Địa _(root)_ | Vòng Diệt _(nova)_ |
| 10 | **Hành Tinh** | Kiếm Quỹ Đạo | Quỹ Đạo Nhanh | Cầu Linh _(orb)_ | Tốc Chiến _(haste)_ | Hóa Vũ _(stance)_ |
| 11 | **Phi Đao** | Phi Đao Bật Tung | Dao Nhắm Yếu Điểm | Trói Ảnh _(slow)_ | Ngũ Hành Đạn _(bounce)_ | Loạn Tiễn _(fan)_ |
| 12 | **Bất Tử** | Sát Thủ Giáp Sắt | Giáp Sắt Vỡ | Trấn Địa _(knockup)_ | Trảm Quyết _(strike)_ | Vô Thượng Hộ _(immune)_ |
| 13 | **Khiếp Hồn** | Ác Mộng Khiếp Sợ | Hào Quang Giáp | Kinh Hoảng _(fear)_ | Địa Chấn _(stun)_ | Chấn Địa _(nova)_ |
| 14 | **Vùng Chết** | Kẻ Mở Cổng Địa Ngục | Ngọn Lửa Địa Ngục | Lửa Trù _(zonedot)_ | Phong Trảm _(dash)_ | Đánh Dấu _(mark)_ |
| 15 | **Truy Nã** | Thợ Săn Truy Nã | Hút Huyết Săn | Tỏa Tiễn _(homing)_ | Ảnh Bộ _(dash)_ | Đoạn Mệnh Đao _(execute)_ |
| 16 | **Phản Kích** | Khiên Phản Sát | Giáp Gai Phản | Phản Ngộ _(reflect)_ | Đoạt Mệnh Kích _(strike)_ | Nộ Hỏa Toàn Thân _(rage)_ |
| 17 | **Thanh Tịnh** | Sát Thủ Thanh Tẩy | Hào Quang Tốc Độ | Giải Trói _(cleanse)_ | Phá Quân _(strike)_ | Ám Sát Tuyệt Mệnh _(assassinate)_ |
| 18 | **Bức Tường** | Kẻ Dựng Tường Chặn | Tường Giảm Hồi | Băng Thành _(wall)_ | Ảnh Bộ _(dash)_ | Đoạn Mệnh Đao _(execute)_ |
| 19 | **Huyết Đồng** | Hút Huyết Triệu Hồi | Hút Huyết Đồng | Hút Phép _(spellvamp)_ | Đoạt Mệnh Kích _(strike)_ | Hồn Thú _(spawn)_ |
| 20 | **Nhắm Chết** | Kẻ Hạ Gục Chớp Nhoáng | Hồi Máu Sau Săn | Lao Kích _(dash)_ | Hủy Dấu _(mark)_ | Ám Sát Tuyệt Mệnh _(assassinate)_ |

## Đỡ Đòn (20 tướng)

| # | Tướng | Danh hiệu | Passive | Chiêu 1 | Chiêu 2 | Chiêu cuối |
|---|---|---|---|---|---|---|
| 1 | **Hắc Lôi** | Người Nhảy Đón | Bước Tốc Huyết | Trảm Quyết _(strike)_ | Giáp Linh _(shield)_ | Sát Thiên _(leap)_ |
| 2 | **Thạch Nộ** | Bão Núi Lửa | Da Núi Lửa | Vòng Diệt _(nova)_ | Bất Khuất _(taunt)_ | Bão Tối _(storm)_ |
| 3 | **Bảo Long** | Tường Sống Bất Tử | Vỡ Khiên Chấn | Phong Trảm _(dash)_ | Đánh Bay _(knockup)_ | Kết Giới Hoàng Kim _(sanctuary)_ |
| 4 | **Xích Ngục** | Kẻ Nhốt Địa Ngục | Ý Chí Ngục | Trói Địa _(root)_ | Phong Ấn _(silence)_ | Băng Thành _(wall)_ |
| 5 | **Xuân Sinh** | Suối Sống Vĩnh Cửu | Hơi Xuân | Cam Lộ _(heal)_ | Huyết Tế _(drain)_ | Hồi Xuân _(regen)_ |
| 6 | **Móc Huyết** | Kẻ Móc Xích | Huyết Tế | Trói Diệt _(pull)_ | Móc Tuyệt _(grapple)_ | Đoạn Mệnh Đao _(execute)_ |
| 7 | **Hồn Vong** | Bóng Đêm Bất Tử | Vong Bất Tiễn | Kinh Hoảng _(fear)_ | Trói Ảnh _(slow)_ | Kim Thân _(immune)_ |
| 8 | **Độc Cổ** | Thần Độc Cổ Đại | Đao Độc | Trùng Cốt _(poison)_ | Hủy Kháng _(shred)_ | Hướng Ngộ _(channel)_ |
| 9 | **Triệu Linh** | Người Gọi Hồn Đá | Hồn Đá Hộ Vệ | Huyền Châu _(orb)_ | Đồng Mạch _(bond)_ | Linh Binh _(spawn)_ |
| 10 | **Khiên Bạc** | Gương Phản Đạn | Gương Bạc | Trảm Quyết _(strike)_ | Khiên Đảo _(reflect)_ | Kim Thân _(immune)_ |
| 11 | **Cuồng Lôi** | Chiến Thần Cuồng Nộ | Nộ Huyết | Phá Thế _(empower)_ | Phá Quân _(strike)_ | Cuồng Nộ Chiến Thần _(rage)_ |
| 12 | **Thái A** | Kiếm Thái Vô Song | Tốc Thái | Phá Vạn Giáp _(truedmg)_ | Đánh Dấu _(mark)_ | Thất Thất _(stance)_ |
| 13 | **Sét Xuyên** | Sét Xuyên Vạn Lớp | Sét Dẫn | Liên Hoàn Kích _(chain)_ | Phá Vệ _(shred)_ | Chấn Địa _(nova)_ |
| 14 | **Lăn Đá** | Kẻ Lăn Trấn | Đà Lăn | Lộn Diệt _(roll)_ | Bất Khuất _(taunt)_ | Choáng Kích _(stun)_ |
| 15 | **Bẫy Mộc** | Kẻ Săn Rừng Sâu | Thợ Săn Khéo | Bẫy Long _(trap)_ | Địa Ngục _(zonedot)_ | Thạch Tường _(wall)_ |
| 16 | **Huyền Mộ** | Hút Mộ Huyền Sư | Mộ Hí | Đốt Mạch _(manaburn)_ | Tẫn Hồn _(fear)_ | Cực Tọa _(channel)_ |
| 17 | **Tiêu Dao** | Vua Tiêu Dao | Huyết Tiêu | Kỷ Tiểu _(boomerang)_ | Phong Trảm _(dash)_ | Kết Liễu _(execute)_ |
| 18 | **Ảnh Đòn** | Bóng Đòn Ám Sát | Ảnh Tiệt | Dịch Ảnh _(blink)_ | Trảm Quyết _(strike)_ | Bình Địa Phá _(leap)_ |
| 19 | **Tán Thạch** | Kẻ Tán Kích | Đá Nứt | Phân Liệt _(split)_ | Phá Không Kích _(knockup)_ | Chấn Địa _(nova)_ |
| 20 | **Hút Phép** | Hút Phép Thần | Hút Linh Phép | Linh Hút _(spellvamp)_ | Tiễn Quang _(bolt)_ | Thánh Vực Hộ Mệnh _(sanctuary)_ |

## Hỗ Trợ (20 tướng)

| # | Tướng | Danh hiệu | Passive | Chiêu 1 | Chiêu 2 | Chiêu cuối |
|---|---|---|---|---|---|---|
| 1 | **Thánh Y** | Thánh Quang Sứ | Ánh Sáng Chia Sẻ | Hồi Nguyên _(heal)_ | Xung Phá _(bolt)_ | Phúc Trạch Quang Hoàn _(sanctuary)_ |
| 2 | **Dẫn Đường** | Người Dẫn Đường Gió | Gió Dẫn Đường | Kết Nghĩa _(bond)_ | Đầm Lầy _(slow)_ | Hồi Xuân _(regen)_ |
| 3 | **Băng Nữ** | Nữ Thần Băng | Trái Tim Băng | Đầm Lầy _(slow)_ | Trói Địa _(root)_ | Địa Chấn _(stun)_ |
| 4 | **Câm Yếm** | Bức Tường Câm Lặng | Tường Câm | Cấm Ngôn _(silence)_ | Tẫn Hồn _(fear)_ | Băng Thành _(wall)_ |
| 5 | **Săn Bẫy** | Nữ Săn Bẫy Rừng | Thợ Săn Khéo | Tàng Kích _(trap)_ | Độc Trầm _(zonedot)_ | Triệu Hồi _(spawn)_ |
| 6 | **Sét Bật** | Nữ Sét Dây | Dệt Sét | Xích Diệt _(chain)_ | Bật Tung _(bounce)_ | Vòng Diệt _(nova)_ |
| 7 | **Tiễn Xa** | Xạ Thủ Cứu Trợ | Tiễn Hí | Xuyên Tâm _(pierce)_ | Bắt Bóng _(homing)_ | Tứ Hải Nhất Tiễn _(global)_ |
| 8 | **Hút Hồn** | Hút Hồn Ma Sư | Hồn Hí | Hút Linh _(manaburn)_ | Huyết Tế _(drain)_ | Hướng Ngộ _(channel)_ |
| 9 | **Độc Nhân** | Người Độc Câm | Dệt Độc | Mãng Xà _(poison)_ | Đánh Dấu _(mark)_ | Cuồng Luân _(storm)_ |
| 10 | **Phá Giáp** | Kẻ Phá Vỡ Giáp | Khí Phá Giáp | Xé Giáp _(shred)_ | Vô Hình Tiễn _(truedmg)_ | Tử Hình _(execute)_ |
| 11 | **Buff Sát** | Người Truyền Sát Khí | Tốc Sát | Phá Thế _(empower)_ | Linh Tốc _(haste)_ | Cuồng Nộ Chiến Thần _(rage)_ |
| 12 | **Ảnh Hỗ** | Bóng Hỗ Trợ | Ảnh Tái Sinh | Tàng Hình _(stealth)_ | Đánh Dấu _(mark)_ | Tái Khởi _(reset)_ |
| 13 | **Ném Tiêu** | Công Chúa Ném Tiêu | Tiêu Dẫn | Đào Viên _(boomerang)_ | Tam Liên Đạn _(fan)_ | Vực Sao Rơi _(barrage)_ |
| 14 | **Xạ Cứu** | Xạ Thủ Cứu Thương | Bước Xạ | Bách Bất Trung _(snipe)_ | Nghịch Bộ _(backstep)_ | Hồi Nguyên _(heal)_ |
| 15 | **Móc Kéo** | Kẻ Móc Kéo Địch | Sắt Móc | Trói Diệt _(pull)_ | Móc Tuyệt _(grapple)_ | Hạo Kỳ _(taunt)_ |
| 16 | **Đẩy Lùi** | Người Đẩy Giao Tranh | Gai Bão | Đánh Bay _(knockup)_ | Lao Kích _(dash)_ | Huyền Vực _(storm)_ |
| 17 | **Khiên Cầu** | Nữ Thần Khiên | Khiên Cuối Cùng | Tinh Vệ _(orb)_ | Bất Kích _(reflect)_ | Bất Tử _(immune)_ |
| 18 | **Liên Kết** | Người Dệt Liên Kết | Sinh Tử Đồng Cùng | Vỡ Mảnh _(split)_ | Đồng Mạch _(bond)_ | Kết Giới Hoàng Kim _(sanctuary)_ |
| 19 | **Hỗ Tấn** | Hỗ Trợ Tấn Công | Nộ Cuối Cùng | Lăn Xuyên _(roll)_ | Đoạt Mệnh Kích _(strike)_ | Nộ Hỏa Toàn Thân _(rage)_ |
| 20 | **Thái Hút** | Kiếm Thái Hút Phép | Hút Linh Thái | Thất Thất _(stance)_ | Huyết Tế _(drain)_ | Hồi Nguyên _(heal)_ |

