# 🍃 Wafer Robot Arm – Non-Contact Pick-and-Place
_Raspberry Pi 5 + TB6600 (3-Axis) + Bernoulli Gripper_

---

## 1. Project Overview
| 항목 | 내용 |
|------|------|
| **Goal** | 🔧 _300 mm wafer를 비접촉으로 안전 이송_ |
| **Top Controller** | Raspberry Pi 5 (Python 3 + lgpio) |
| **Drivers / Motors** | TB6600 × 3 + NEMA 17 |
| **End-Effector** | Bernoulli / Cyclone air gripper |
| **Core Modules** | `camera.py` · `vision.py` · `ik.py` · `planner.py` · `motor.py` |

---

## 2. Hardware BOM
| Qty | Part | Spec | 용도 |
|-----|------|------|------|
| 1 | Raspberry Pi 5 | 4 GB | 상위 제어기 |
| 3 | TB6600 Driver | 공통 애노드 | 3축 |
| 3 | NEMA 17 | 1.8°, 2 A | θ₀·θ₁·θ₂ |
| 1 | SMPS | 24 V 8 A | 모터/그리퍼 |
| 1 | Air Gripper | 🔧 | 비접촉 픽업 |
| … | … | … | … |

---

## 3. Pin Map (X-Axis 예시)
| Pi 5 (BCM) | TB6600 | 기능 |
|------------|--------|------|
| GPIO 17 | PUL- | 스텝 |
| GPIO 27 | DIR- | 방향 |
| GPIO 22 | ENA- | 활성 |
| 3V3 | PUL+/DIR+/ENA+ | 공통 애노드 |
| GND | GND | 기준 전위 |

---

## 4. Software Stack
```text
Python 3.11
├─ lgpio          # Pi5 GPIO
├─ opencv-python  # Vision
├─ numpy / scipy  # IK & Planner
└─ pytest         # Tests
