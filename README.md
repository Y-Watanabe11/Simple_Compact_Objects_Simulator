# Compact Objects Simulator（厳密計算版）

## 概要
**Compact Objects Simulator（厳密計算版）**は、ブラックホール・中性子星・白色矮星などのコンパクト天体の物理パラメータと、それに基づく物理量や重力波波形をリアルタイムで可視化するインタラクティブWebアプリケーションです。Three.js による 3D 描画と、物理パネル・重力波パネル・イベントログを組み合わせ、パラメータ変更が即座に結果に反映されます。

---

## 主な機能
- **3D表示**：天体・降着円盤などを Three.js で描画  
- **物理パネル**：  
  - 質量、降着率、スピン、磁場、距離などの入力  
  - Schwarzschild 半径、Eddington 光度、降着光度、最大温度などをリアルタイム計算  
- **重力波チャープ波形パネル**：  
  - 等質量連星系の周波数進化（Inspiral 部分）を数値積分して波形を生成  
  - 距離・チャープ質量・ISCO 周波数・未正規化ピーク値を動的表示  
- **イベントログ**：シミュレーション中のイベントや計算更新の履歴を表示  
- **レイアウト最適化**：物理パネル（右上）→波形パネル（その下）→イベントログ（最下段）。3D キャンバスは縦 72% に縮小し UI の重なりを回避

---

## 理論的背景
### ブラックホール
- **Schwarzschild 半径**: $R_s = 2GM/c^2$  
- **Eddington 光度**: $L_{\rm Edd} = 4\pi GM m_p c / \sigma_T$  
- **降着光度**: $L_{\rm acc} = \eta\,\dot M c^2$  
- **薄い円盤の温度分布**（Shakura–Sunyaev）

### 中性子星
- **ライトシリンダー半径**: $R_L = c/\Omega$  
- **スピンダウン光度**（磁気双極子放射のオーダー）

### 重力波（連星中性子星）
- **チャープ質量**: $M_c=\frac{(m_1 m_2)^{3/5}}{(m_1+m_2)^{1/5}}$  
- **周波数進化**: $\dfrac{df}{dt} \propto f^{11/3}$  
- **ISCO 周波数**: $f_{\rm ISCO} \approx \dfrac{c^3}{6^{3/2}\pi G (m_1+m_2)}$

---

## インストール & 実行方法
1. このリポジトリをクローン  
    ```bash
    git clone https://github.com/username/compact-objects-simulator.git
    cd compact-objects-simulator
    ```
2. 任意のローカル Web サーバーで実行  
    ```bash
    python3 -m http.server 8000
    ```
3. ブラウザで以下にアクセス  
    ```
    http://localhost:8000
    ```

---

## ファイル構成
- `index.html`：アプリ本体  
- `style.css`：レイアウト、パネル配置（UI 重なり回避済み）  
- `main.js`：Three.js 描画、物理計算、イベント処理  

---

## 今後の拡張案
- Kerr BH モデル導入（スピン依存 ISCO、放射効率）  
- 多温度黒体ディスクのスペクトル合成表示  
- 高次 PN や IMRPhenom 系モデルでの重力波生成  
- 検出器感度曲線の重ね合わせと SNR 概算  


---

# Compact Objects Simulator (Precise Calculation Version)

## Overview
**Compact Objects Simulator (Precise Calculation Version)** is an interactive web application that visualizes the physics of compact objects (black holes, neutron stars, white dwarfs) and renders derived quantities and gravitational waveforms in real time. It uses Three.js for 3D rendering with a physics panel, a GW waveform panel, and an event log, so parameter updates are reflected instantly.

---

## Key Features
- **3D Visualization** of compact objects and accretion disks (Three.js)  
- **Physics Panel**:  
  - Inputs: mass, accretion rate, spin, magnetic field, distance  
  - Outputs: Schwarzschild radius, Eddington luminosity, accretion luminosity, disk $T_{\max}$ (updated live)  
- **GW Chirp Panel**:  
  - Equal-mass inspiral frequency evolution via numerical integration  
  - Dynamic display of distance, chirp mass, ISCO frequency, and unnormalized peak amplitude  
- **Event Log** for simulation updates and events  
- **Optimized Layout**: physics (top-right) → waveform (below) → log (bottom). 3D canvas height reduced to ~72% to avoid overlap

---

## Theoretical Background
### Black Holes
- **Schwarzschild Radius**: $R_s = 2GM/c^2$  
- **Eddington Luminosity**: $L_{\rm Edd} = 4\pi GM m_p c / \sigma_T$  
- **Accretion Luminosity**: $L_{\rm acc} = \eta\,\dot M c^2$  
- **Thin Disk Temperature** (Shakura–Sunyaev)

### Neutron Stars
- **Light Cylinder**: $R_L=c/\Omega$  
- **Spin-down Luminosity** (magnetic dipole order)

### Gravitational Waves (BNS)
- **Chirp Mass**: $M_c=\frac{(m_1 m_2)^{3/5}}{(m_1+m_2)^{1/5}}$  
- **Frequency Evolution**: $\dfrac{df}{dt}\propto f^{11/3}$  
- **ISCO Frequency**: $f_{\rm ISCO}\approx \dfrac{c^3}{6^{3/2}\pi G (m_1+m_2)}$

---

## Installation & Usage
1. Clone the repository  
    ```bash
    git clone https://github.com/username/compact-objects-simulator.git
    cd compact-objects-simulator
    ```
2. Run a local web server  
    ```bash
    python3 -m http.server 8000
    ```
3. Open in your browser  
    ```
    http://localhost:8000
    ```

---

## File Structure
- `index.html`: main app  
- `style.css`: layout & panels (overlap-free)  
- `main.js`: Three.js rendering, physics, events  

---

## Future Enhancements
- Kerr BH: spin-dependent ISCO and efficiency  
- Multi-temperature blackbody disk spectrum  
- Higher-order PN & IMRPhenom-based GW models  
- Detector sensitivity overlays & SNR estimates  
