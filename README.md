# 🏀 **농구 게임 프로젝트 (Vanilla JS → jQuery)**

![basketball-game](https://img.shields.io/badge/상태-완료-brightgreen) ![version](https://img.shields.io/badge/버전-3.0-blue)  

---

## 📋 **목차**
- [🎯 개요](#-개요)  
- [💡 프로젝트 발전 과정](#-프로젝트-발전-과정)  
- [📦 주요 기능](#-주요-기능)  
- [💻 코드 비교](#-코드-비교)  
- [📚 배운 점](#-배운-점)  
- [🚀 설치 및 실행](#-설치-및-실행)  
- [📜 감사의 말](#-감사의-말)  

---

## 🎯 **개요**
이 프로젝트는 사용자와 컴퓨터가 번갈아가며 슛을 던져 더 높은 점수를 얻는 **턴제 농구 게임**입니다. 각 플레이어는 제한된 횟수 안에서 최대한 많은 점수를 획득해야 하며, 컴퓨터의 AI는 점수 차이에 따라 슛 성공 확률이 달라집니다.  

- **초기 버전:** Vanilla JavaScript (수동 DOM 조작 및 이벤트 처리)  
- **리팩토링 버전:** 반복 코드 최소화 및 함수화를 통한 가독성 개선  
- **최종 버전:** **jQuery**를 사용하여 더 간결하고 효율적인 코드 작성, 플러그인을 통한 부드러운 애니메이션 추가  

---

## 💡 **프로젝트 발전 과정**  

| 🧩 **버전** | 🚀 **변경 사항 및 개선점** |
|-------------|----------------------------|
| **v1.0** - Vanilla JS | `getElementById()`와 `innerHTML`을 사용한 수동 DOM 조작 및 기본 이벤트 처리 |
| **v2.0** - 코드 리팩토링 | 반복되는 코드를 함수로 모듈화하고, 게임 로직을 객체화하여 유지보수성 향상 |
| **v3.0** - jQuery 도입 ✅ | `$()`를 사용한 간결한 DOM 접근, `.on()`을 통한 효율적인 이벤트 처리 및 `.fadeIn()`과 `.fadeOut()`으로 부드러운 애니메이션 적용 |

---

## 📦 **주요 기능**
✅ **턴제 슛팅:** 사용자와 컴퓨터가 번갈아가며 슛을 시도  
✅ **실시간 점수 업데이트:** DOM을 통해 즉각적으로 점수 표시  
✅ **AI 난이도 조정:** 점수 차이에 따라 AI의 슛 성공 확률 변화  
✅ **부드러운 애니메이션:** `.fadeIn()`, `.fadeOut()`, `animateNumber` 플러그인 활용  
✅ **직관적인 게임 조작:** 버튼 클릭으로 쉽게 게임 진행 가능  

---

## 💻 **코드 비교**

### **1. DOM 선택**
| **방법** | **Vanilla JavaScript** | **jQuery** |
|----------|------------------------|------------|
| **ID로 요소 선택** | `document.getElementById('user-score').innerHTML = 20;` | `$('#user-score').html(20);` |
| **클래스로 요소 선택** | `document.getElementsByClassName('btn-user')` | `$('.btn-user')` |
| **태그로 요소 선택** | `document.getElementsByTagName('button')` | `$('button')` |

---

### **2. 이벤트 처리**
| **방법** | **Vanilla JavaScript** | **jQuery** |
|----------|------------------------|------------|
| **클릭 이벤트** | `element.addEventListener('click', onShoot);` | `$('#shoot-btn').on('click', onShoot);` |
| **인라인 이벤트** | `<button onclick="onShoot()">` | `<button id="shoot-btn">` + `.on('click', onShoot)` |

---

### **3. 버튼 활성화/비활성화**
| **방법** | **Vanilla JavaScript** | **jQuery** |
|----------|------------------------|------------|
| **활성화/비활성화** | 배열을 반복하며 `.disabled` 속성 설정 | `$('.btn-user').prop('disabled', true);` |
| **단일 요소** | `element.disabled = false;` | `$('#shoot-btn').prop('disabled', false);` |

---

### **4. 애니메이션과 텍스트 업데이트**
```javascript
// Vanilla JS
document.getElementById('text').innerHTML = '슛 성공!';
```
```javascript
// jQuery + 페이드 효과
$('#text').fadeOut(300, function() {
    $(this).html('슛 성공!').fadeIn(100);
});
```

---

### **5. AI 로직 (점수 차이에 따라 성공 확률 변경)**
```javascript
if (difference > 11) {
    computer.percent2 = 0.7;
    computer.percent3 = 0.43;
} else if (difference > 7) {
    computer.percent2 = 0.6;
    computer.percent3 = 0.38;
} else if (difference < -11) {
    computer.percent2 = 0.3;
    computer.percent3 = 0.23;
} else if (difference < -7) {
    computer.percent2 = 0.4;
    computer.percent3 = 0.28;
}
```

---

## 💎 **jQuery의 장점**
| **기능**                     | **Vanilla JavaScript**                               | **jQuery**                                      |
|------------------------------|---------------------------------------------------|----------------------------------------------|
| **코드 가독성**              | 코드가 길고 반복적임                               | 짧고 직관적인 체이닝 방식으로 간결함         |
| **이벤트 처리**              | 요소마다 `addEventListener()`를 개별 작성해야 함  | `.on()`으로 다수 요소에 일괄 이벤트 적용    |
| **DOM 선택**                 | `getElementById`, `getElementsByClassName` 사용    | CSS 선택자 방식으로 `$()`로 통합             |
| **애니메이션**               | CSS 전환이나 JS 직접 조작 필요                     | `.fadeIn()`, `.fadeOut()` 등 내장 함수 사용 |
| **속성 제어**                | `.disabled`, `.style` 등을 개별 조작해야 함        | `.prop()`, `.css()`, `.html()`로 간편하게 제어 |
| **브라우저 호환성**          | 구버전 브라우저에서 일부 기능 미지원               | 구버전 호환성 우수                           |

---

## 📚 **배운 점**
### ✅ **주요 학습 내용**
- **DOM 조작의 효율성:** jQuery는 더 짧고 직관적인 문법으로 DOM을 쉽게 조작할 수 있음  
- **이벤트 처리의 간소화:** `.on()` 메서드로 코드가 더욱 간결해짐  
- **코드 재사용성 향상:** 반복적인 코드 블록을 함수화하고, 관련 데이터를 객체로 그룹화함  
- **UI/UX 개선:** `fadeIn()`, `fadeOut()` 등의 애니메이션으로 사용자 경험이 향상됨  
- **게임 로직의 향상:** AI가 점수 차이에 따라 전략적으로 슛을 시도하여 게임의 흥미를 더함  

---

### 📌 **향후 개선 사항**
- **웹 스토리지 기능:** `localStorage`를 사용하여 최고 점수를 기록  
- **멀티플레이어 모드:** 사용자 간 대결 기능 추가  
- **현대적인 프레임워크 적용:** React 또는 Vue.js를 통해 더 세련된 UI 제공  

---

## 🚀 **설치 및 실행**
```bash
# 1. 레포지토리 클론
git clone https://github.com/sungjm/basketball_game_jquery.git

# 2. 프로젝트 폴더로 이동
cd basketball_game_jquery

# 3. index.html 파일을 브라우저로 열어서 게임 실행
```

---

## 📜 **새로 배운 점**
🎯 **jQuery:** 직관적인 DOM 조작과 이벤트 처리 제공  
🎨 **AnimateNumber.js:** 부드러운 점수 애니메이션 구현에 도움  
💡 **학습 과정:** Vanilla JS부터 jQuery까지의 전환을 통해 효율적인 코드 작성법 습득  

---

## 🤝 **기여 방법**
프로젝트에 기여를 원하시면 **이슈**를 등록하거나 **풀 리퀘스트(PR)**를 제출해 주세요.  
도움이 되셨다면 **GitHub 저장소에 ⭐️ 스타를 눌러주세요!**  