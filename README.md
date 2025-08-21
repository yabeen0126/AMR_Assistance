# 🤖 AMR 기반 간호 어시스턴트 로봇
![작동 영상](https://github.com/mjw3723/nursing_assistance_robot/raw/main/img/demo_video.gif)
---

## 📄프로젝트 개요
의료 현장의 간호사 업무 과중 및 인력 부족 문제를 해결하기 위해, SLAM 기반 자율주행 기술을 활용한 간호 보조 로봇 시스템을 개발한다. 본 시스템은 **조제실 로봇**과 **병동 로봇**으로 구성되어 약품 전달, 환자 생체 징후 확인 등 반복적인 업무를 자동화함으로써, 간호사가 환자 케어와 같은 전문적인 업무에 더 집중할 수 있는 환경을 조성하는 것을 목표로 한다.

---

## 🔍 Architecture

![시스템 아키텍처](https://i.imgur.com/example.png)  
*<-- 프로젝트 PDF 11페이지의 시스템 아키텍처 이미지를 삽입하세요 -->*

![노드 아키텍처](https://i.imgur.com/example2.png)  
*<-- 프로젝트 PDF 12페이지의 노드 아키텍처 이미지를 삽입하세요 -->*

---

### 📅 개발기간
- 2024.06.23 ~ 2024.07.03 (총 11일)

---

## 🧑 팀원
- **백홍하(팀장)**: `/robot4/Vision`, 모니터링 GUI, EMQX Cloud 통신
- **이하빈**: `/robot4/Vision`
- **장연호**: `/robot4/Navigation`
- **정찬원**: `/robot4/Navigation`
- **문준웅**: `/robot1/Navigation`, 모니터링 GUI
- **이경민**: `/robot1/Vision`
- **정민섭**: `/robot1/Navigation`, 바이탈 체크 기능 개발
- **최정호**: `/robot1/Vision`

---

## ⚙️ 개발 환경
### 🤖 Robotics & Hardware
![RASPBERRY PI](https://img.shields.io/badge/Raspberry%20Pi-A22846?style=for-the-badge&logo=Raspberry%20Pi&logoColor=white) ![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
- **Robot:** TurtleBot4
- **Camera:** OAK-D Camera
- **Sensor:** RP LIDAR

### 💻 Software & AI
![PYTHON](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white) <img src="https://img.shields.io/badge/ROS2%20Humble-5A7594?style=for-the-badge&logo=ros&logoColor=white"> <img src="https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white"> <img src="https://img.shields.io/badge/Yolo%20V8-2871E5?style=for-the-badge&logo=OpenCV&logoColor=white"> ![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
- **Frameworks & Middleware:** ROS2 Humble, EMQX (MQTT)
- **AI & Vision:** YOLOv8s, OpenCV, TensorFlow, Roboflow
- **GUI:** Tkinter, Qt

---

## 📄 ER Diagram
*[요청에 따라 Mermaid 다이어그램을 삭제했습니다.]*

---

## ⭐ 주요 기능

- **듀얼 로봇 시스템 및 클라우드 통신**
  - **'조제실 로봇'**과 **'병동 로봇'** 두 대를 분리하여 임무 수행 효율을 극대화함.
  - 네트워크 부하를 줄이고 안정적인 통신을 위해 두 로봇을 물리적으로 다른 네트워크에 배치하고, **EMQX Cloud(MQTT)**를 통해 상태와 데이터를 교환함.

- **조제실 로봇 (`/robot4`)**
  - **약품 탐지 및 위치 추정**: GUI를 통해 약품 배송 요청을 받으면, Nav2를 이용해 약품 선반으로 이동함. YOLOv8s 모델로 처방된 약품을 정확하게 탐지하고, OAK-D 카메라의 Depth 정보를 이용해 약품의 3D 좌표를 `map` 좌표계로 변환하여 위치를 특정함.
  
- **병동 로봇 (`/robot1`)**
  - **안전 주행 및 환자 식별**: 복도 주행 중 YOLO를 이용해 환자나 휠체어 등 장애물을 인식하면 자동으로 정지하고, TTS로 비켜줄 것을 요청함. 병실 앞에 도착하면 배정된 환자 ID에 맞는 아르코 마커를 탐지하여 정확한 대상에게 약을 전달함.
  - **비접촉 바이탈 체크 (rPPG)**: 환자에게 약을 전달한 후, OAK-D 카메라로 환자의 얼굴을 촬영함. **rPPG 기술**을 활용하여 영상에서 피부색의 미세한 변화를 분석, 심박수와 혈압 등 생체 신호를 비접촉으로 측정하고 GUI에 전송함.

---

## 🎬 프로젝트 결과물
### 메인 컨트롤러 GUI
  <img src="https://i.imgur.com/example3.png" width="800"/>
  *<-- 프로젝트 PDF 15, 20페이지의 GUI 이미지를 삽입하세요 -->*
  
### 자율주행 및 약품 탐지
  <img src="https://i.imgur.com/example4.png" width="800"/>
  *<-- 프로젝트 PDF 13, 26페이지의 맵 및 YOLO 탐지 이미지를 삽입하세요 -->*
  
### 듀얼 로봇 연동 (랑데부)
  <img src="https://i.imgur.com/example5.png" width="800"/>
  *<-- 프로젝트 PDF 37페이지의 로봇 연동 이미지를 삽입하세요 -->*
  
### 환자 인식 및 바이탈 체크
  <img src="https://i.imgur.com/example6.png" width="800"/>
  *<-- 프로젝트 PDF 64, 68페이지의 얼굴 인식 및 바이탈 그래프 이미지를 삽입하세요 -->*
