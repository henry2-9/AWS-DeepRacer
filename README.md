# AWS-DeepRacer
## 🧪 初始穩定模型（v0.1）

這是最早訓練成功並穩定完賽的模型，使用**簡單且保守的獎勵函數**與**基礎動作空間**。雖然圈速未達極致，但非常適合作為 baseline 或 fine-tune 基底。

---

### ✅ 訓練結果圖（穩定成長）

![初始訓練結果圖](images/stable-training.png)

- **Best lap**：`11.062 秒`
- **Progress**：`100.00%`
- 獎勵逐步上升，完成率穩定，成功完賽

---

### 🔍 評估影片截圖

![初始模型影片](images/stable-eval.png)

- 可觀察到車輛順利貼近中心線行駛
- 雖速度不快，但幾乎無出界、穩定完賽

---

### ⚙️ 模型設定摘要

- 賽道：`re:Invent 2018（逆時針）`
- 訓練時間：120 分鐘
- 演算法：PPO
- 動作空間：10 組（基礎彎道 + 部分直線）
- 學習率：`0.0003`

#### 📌 動作空間範例：

| 角度 (°) | 速度 (m/s) |
|----------|-------------|
| -30      | 1.0 / 1.5    |
| -15      | 1.5 / 2.0    |
| 0        | 3.0 / 4.0    |
| 15       | 1.5 / 2.0    |
| 30       | 1.5          |

---

### 🧠 使用的獎勵函數（v0.1）

```python
def reward_function(params):
    all_wheels_on_track = params['all_wheels_on_track']
    distance_from_center = params['distance_from_center']
    track_width = params['track_width']

    reward = 1e-3

    if all_wheels_on_track and (0.5 * track_width - distance_from_center) >= 0.05:
        reward = 1.0

    return float(reward)
