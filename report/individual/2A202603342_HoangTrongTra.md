# Báo cáo Day 14 — Hoang Trong Tra — 2A202603342

- Mã học viên dùng với `--student`: `2A202603342`
- `seed_tag` trong `frames_A.txt`: `82ac3100fd`
- Mình dùng AI hỗ trợ đối chiếu camera/LiDAR, chỉnh cuboid trên CVAT và ghi báo cáo. Mình đã kiểm lại nhãn tập A trên CVAT.

## 1. Dự đoán trước sweep (bước 5b)

- Mình dự đoán tăng `score_thr` từ `0.1` lên khoảng `0.5` sẽ giảm chi phí sửa nhiều nhất trong lưới thử. Mình dự đoán giữ `min_points=0` vì ít thấy hộp có rất ít điểm trong kết quả ban đầu.
- Trên ảnh BEV và camera tập A, mình thấy nhiều hộp bám vào cây, hàng rào và vật cố định. Cấu hình gốc có 72 hộp cần xóa, 1 vật cần thêm và 2 hộp cần sửa, với chi phí 23,6. Trung vị score là 0,362 ở nhóm hộp không ghép được và 0,800 ở nhóm ghép được. Tăng ngưỡng có thể lọc nhiều hộp dư. Một số vật thật có score thấp cũng có thể bị lọc, nên mình sẽ kiểm tra cả cột thêm khi so sánh.

## 2. Tập A: sửa tay và tune

| Cấu hình | Xóa | Thêm | Sửa | Chi phí |
|---|---:|---:|---:|---:|
| Gốc | | | | |
| `best_config.json` | | | | |

- Tham số đã đổi trong `best_config.json`: ...
- Kết quả leave-one-out (dán các dòng `scripts/pp_sweep.py` in ra): ...
- Cấu hình có ổn định trên từng frame không? Vì sao tôi vẫn chọn (hoặc không chọn) nó: ...

## 3. Trước/sau (bước 8)

![so sánh](../../d14_<ID>/compare/<frame>.jpg)

- `scripts/pp_compare.py` báo giảm (hoặc tăng) ...% công sửa trên tập A.
- Dự đoán ở mục 1 đúng hay sai? Giải thích bằng số box xóa/thêm/sửa: ...

## 4. Tập B

Số đo từ `scripts/pp_prelabel.py --frames d14_<ID>/frames_B.txt --config d14_<ID>/best_config.json --gt d14_<ID>/ref_B.json`:

| Xóa | Thêm | Sửa | Chi phí |
|---:|---:|---:|---:|
| | | | |

- Loại box tốn công sửa nhất ở tập B: ...

## 5. Giới hạn

- Nêu ít nhất 2 giới hạn (ví dụ: chỉ 3 frame tune; model KITTI không có Truck/Bus; chi phí là công thức, chưa phải thời gian sửa thật): ...
