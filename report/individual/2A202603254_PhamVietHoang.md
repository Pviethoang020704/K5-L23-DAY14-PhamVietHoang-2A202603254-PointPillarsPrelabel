# Báo cáo Day 14 — Phạm Việt Hoàng — 2A202603254

- Mã học viên dùng với `--student`: `2A202603254`
- `seed_tag` trong `frames_A.txt`: `82ac3100fd`

## 1. Dự đoán trước sweep (bước 5b)

- Tham số tôi nghĩ giảm công sửa nhiều nhất: `score_thr`. Tôi dự đoán tăng `score_thr` lên 0.4 và đặt `min_points=5` sẽ giúp giảm công sửa.

- Vì sao: Khi quan sát ảnh BEV và chỉnh sửa trên CVAT, tôi thấy mô hình sinh nhiều cuboid thừa, đặc biệt là lớp Cyclist tại các khu vực cây xanh và ven đường. Ở frame s01f59, số cuboid giảm từ 42 xuống còn 18 sau khi chỉnh sửa, trong đó Cyclist giảm từ 19 xuống còn 4. Tôi dự đoán tăng ngưỡng confidence và lọc các cuboid có ít điểm LiDAR sẽ giảm số hộp cần xóa. Tuy nhiên, ngưỡng quá cao có thể làm mất các vật thể thật bị che khuất hoặc có ít điểm LiDAR.
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
