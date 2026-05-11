<div class="perspective-calc-container" style="max-width:600px; margin:0 auto; font-family:system-ui, -apple-system, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; color:#1e293b;">
  <style>
    /* 内部样式，只作用于本计算器，不影响博客全局 */
    .perspective-calc-container * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }
    .perspective-calc-container .card {
        background: #ffffff;
        border-radius: 24px;
        padding: 20px 18px;
        margin-bottom: 20px;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.02), 0 1px 2px rgba(0, 0, 0, 0.03);
        border: 1px solid #eef2f6;
    }
    .perspective-calc-container .card-header {
        font-weight: 600;
        font-size: 1.2rem;
        margin-bottom: 1.2rem;
        padding-bottom: 0.5rem;
        border-bottom: 2px solid #eef2f6;
        display: flex;
        align-items: center;
        gap: 8px;
        flex-wrap: wrap;
        color: #0f172a;
    }
    .perspective-calc-container .card-header span {
        background: #eef2ff;
        padding: 2px 10px;
        border-radius: 40px;
        font-size: 0.75rem;
        font-weight: 500;
        color: #2563eb;
    }
    .perspective-calc-container .row-2col {
        display: flex;
        flex-wrap: wrap;
        gap: 12px;
        margin-bottom: 16px;
    }
    .perspective-calc-container .input-group-half {
        flex: 1;
        min-width: 130px;
    }
    .perspective-calc-container .input-group {
        margin-bottom: 18px;
    }
    .perspective-calc-container .input-row {
        display: flex;
        flex-wrap: wrap;
        align-items: baseline;
        gap: 12px;
        margin-bottom: 12px;
    }
    .perspective-calc-container .input-row label {
        width: 85px;
        font-size: 0.9rem;
        font-weight: 500;
        color: #334155;
    }
    .perspective-calc-container .input-field {
        flex: 1;
        min-width: 140px;
    }
    .perspective-calc-container input, .perspective-calc-container .readonly-input {
        width: 100%;
        padding: 12px 14px;
        font-size: 1rem;
        border: 1px solid #e2e8f0;
        border-radius: 20px;
        background: #fefefe;
        transition: 0.2s;
        font-family: monospace;
        font-weight: 500;
    }
    .perspective-calc-container input:focus {
        outline: none;
        border-color: #3b82f6;
        box-shadow: 0 0 0 3px rgba(59,130,246,0.1);
    }
    .perspective-calc-container .button-group {
        display: flex;
        flex-wrap: wrap;
        gap: 12px;
        margin-top: 8px;
        margin-bottom: 8px;
    }
    .perspective-calc-container .btn {
        flex: 1;
        background: #ffffff;
        border: 1px solid #cbd5e1;
        padding: 12px 16px;
        border-radius: 40px;
        font-size: 1rem;
        font-weight: 500;
        color: #1e293b;
        cursor: pointer;
        transition: all 0.2s;
        text-align: center;
        background: #f8fafc;
    }
    .perspective-calc-container .btn.primary {
        background: #2563eb;
        border-color: #2563eb;
        color: white;
    }
    .perspective-calc-container .btn.primary:active {
        background: #1d4ed8;
        transform: scale(0.97);
    }
    .perspective-calc-container .btn:active {
        transform: scale(0.97);
    }
    .perspective-calc-container .result-box {
        background: #f8fafc;
        border-radius: 20px;
        padding: 16px;
        margin-top: 14px;
    }
    .perspective-calc-container .result-line {
        display: flex;
        justify-content: space-between;
        margin-bottom: 12px;
        font-size: 0.95rem;
        flex-wrap: wrap;
        gap: 6px;
    }
    .perspective-calc-container .result-label {
        font-weight: 500;
        color: #475569;
    }
    .perspective-calc-container .result-value {
        font-family: monospace;
        font-weight: 600;
        color: #0f172a;
        background: #eef2ff;
        padding: 2px 10px;
        border-radius: 24px;
    }
    .perspective-calc-container .warning {
        color: #dc2626;
        font-size: 0.8rem;
        margin-top: 12px;
        background: #fee2e2;
        padding: 8px 12px;
        border-radius: 20px;
        text-align: center;
    }
    .perspective-calc-container .step-hint {
        display: inline-flex;
        align-items: center;
        margin-left: 8px;
        font-size: 0.75rem;
        color: #475569;
        background: #f1f5f9;
        padding: 2px 10px;
        border-radius: 30px;
    }
    @media (max-width: 500px) {
        .perspective-calc-container .row-2col { flex-direction: column; }
        .perspective-calc-container .input-row { flex-direction: column; gap: 6px; }
        .perspective-calc-container .input-row label { width: auto; }
        .perspective-calc-container .result-line { flex-direction: column; gap: 4px; border-bottom: 1px solid #e2e8f0; padding-bottom: 8px; }
        .perspective-calc-container .button-group { flex-direction: column; }
        .perspective-calc-container .step-hint { margin-left: 0; display: inline-block; margin-top: 4px; }
    }
  </style>

  <!-- 标题区（带版本号） -->
  <div class="card" style="text-align: center; background: #ffffff;">
    <h2 style="font-weight: 600; letter-spacing: -0.3px;">📐 透视计算器 <span style="font-size: 0.75rem; background: #eef2ff; padding: 2px 8px; border-radius: 30px; color: #2563eb;">v2.0.1</span></h2>
    <p style="color: #475569; margin-top: 8px; font-size: 0.85rem;">物体纵深运动 → 像素尺寸变化 | 35mm等效视角</p>
  </div>

  <!-- 主输入卡片 -->
  <div class="card">
    <div class="card-header">📷 相机 & 物体参数 <span>基础数据</span></div>
    <div class="row-2col">
      <div class="input-group-half"><label style="display:block; font-size:0.85rem; margin-bottom:6px;">画布宽度(px)</label><input type="number" id="calcCanvasW" value="1920" step="1" placeholder="像素"></div>
      <div class="input-group-half"><label style="display:block; font-size:0.85rem; margin-bottom:6px;">画布高度(px)</label><input type="number" id="calcCanvasH" value="1080" step="1" placeholder="像素"></div>
    </div>
    <div class="row-2col">
      <div class="input-group-half"><label style="display:block; font-size:0.85rem; margin-bottom:6px;">物体宽度(cm)</label><input type="number" id="calcObjW" value="40" step="any" placeholder="厘米"></div>
      <div class="input-group-half"><label style="display:block; font-size:0.85rem; margin-bottom:6px;">物体高度(cm)</label><input type="number" id="calcObjH" value="160" step="any" placeholder="厘米"></div>
    </div>
    <div class="row-2col">
      <div class="input-group-half"><label style="display:block; font-size:0.85rem; margin-bottom:6px;">物距 u (cm)</label><input type="number" id="calcDistance" value="200" step="any" placeholder="厘米"></div>
      <div class="input-group-half"><label style="display:block; font-size:0.85rem; margin-bottom:6px;">焦距 f (mm)</label><input type="number" id="calcFocal" value="50" step="any" placeholder="毫米"></div>
    </div>
    <div class="button-group" style="margin-top:12px;">
      <button id="calcInitBtn" class="btn primary">✨ 计算初始参数</button>
      <button id="calcResetInitialBtn" class="btn">⟳ 重置当前会话</button>
    </div>
  </div>

  <!-- 等效视角 & 初始像尺寸 -->
  <div class="card">
    <div class="card-header">🔍 等效视角 & 初始像尺寸</div>
    <div class="result-box" style="border-left:none; padding:16px 0 0 0; background:transparent;">
      <div class="result-line"><span class="result-label">水平FOV (35mm等效)</span><span class="result-value" id="calcFovH">—</span></div>
      <div class="result-line"><span class="result-label">垂直FOV (35mm等效)</span><span class="result-value" id="calcFovV">—</span></div>
      <div class="result-line"><span class="result-label">📐 初始像宽度(px)</span><span class="result-value" id="calcInitPxW">—</span></div>
      <div class="result-line"><span class="result-label">📏 初始像高度(px)</span><span class="result-value" id="calcInitPxH">—</span></div>
      <div class="result-line"><span class="result-label">📍 当前物距 u (cm)</span><span class="result-value" id="calcCurrentU">—</span></div>
    </div>
  </div>

  <!-- 纵深运动模拟 -->
  <div class="card">
    <div class="card-header">🏃 纵深运动模拟 <span>步长可正/负</span></div>
    <div style="display: flex; flex-wrap: wrap; align-items: center; gap: 12px; margin-bottom: 18px;">
      <div style="flex:2; min-width:140px;"><label style="font-size:0.9rem; font-weight:500;">步长 i (cm)</label><input type="number" id="calcStepLen" value="-60" step="any" style="margin-top:4px;"></div>
      <div style="flex:3; font-size:0.8rem; color:#475569; background:#f1f5f9; padding:8px 12px; border-radius:30px; text-align:center;">💡 靠近为正，远离为负</div>
    </div>
    <div class="button-group">
      <button id="calcMoveStepBtn" class="btn primary">▶ 移动一步</button>
      <button id="calcPrevStepBtn" class="btn">◀ 上一步</button>
    </div>
    <div class="button-group-single" style="margin-top:12px;"><button id="calcNewCalcBtn" class="btn">🔄 全新计算</button></div>
    <div class="step-control" style="margin-top:20px;">
      <div class="result-line"><span class="result-label">已移动步数</span><span class="result-value" id="calcStepCounter">0</span></div>
      <div id="calcStepResultArea" style="margin-top:16px;">
        <div class="result-line"><span class="result-label">✨ 当前像宽(px)</span><span class="result-value" id="calcCurrPxW">—</span></div>
        <div class="result-line"><span class="result-label">✨ 当前像高(px)</span><span class="result-value" id="calcCurrPxH">—</span></div>
        <div class="result-line"><span class="result-label">📉 宽度变化量(px)</span><span class="result-value" id="calcDeltaW">—</span></div>
        <div class="result-line"><span class="result-label">📉 高度变化量(px)</span><span class="result-value" id="calcDeltaH">—</span></div>
        <div class="result-line"><span class="result-label">📊 像宽变化比(%)</span><span class="result-value" id="calcRatioW">—</span></div>
        <div class="result-line"><span class="result-label">📊 像高变化比(%)</span><span class="result-value" id="calcRatioH">—</span></div>
      </div>
    </div>
    <div id="calcWarningMsg" class="warning" style="display:none;"></div>
  </div>

  <!-- 底部超链接（X和B站） -->
  <div style="text-align: center; margin-top: 12px; font-size: 12px; color: #94a3b8;">
    透视计算器 · 模拟物体沿光轴运动时像素尺寸变化<br>
    X：<a href="https://x.com/aiyasu1921" target="_blank" rel="noopener noreferrer" style="color:#1e293b; text-decoration:none; border-bottom:1px dotted #94a3b8;">@aiyasu1921</a>  
      |  
    Bili：<a href="https://space.bilibili.com/501439558" target="_blank" rel="noopener noreferrer" style="color:#1e293b; text-decoration:none; border-bottom:1px dotted #94a3b8;">501439558</a>
  </div>
</div>

<script>
  // 将所有ID加上前缀以避免与博客其他脚本冲突，同时保持功能完整
  (function() {
    // 获取DOM元素（带前缀calc）
    const canvasWInput = document.getElementById('calcCanvasW');
    const canvasHInput = document.getElementById('calcCanvasH');
    const objWInput = document.getElementById('calcObjW');
    const objHInput = document.getElementById('calcObjH');
    const distanceInput = document.getElementById('calcDistance');
    const focalInput = document.getElementById('calcFocal');
    const stepLenInput = document.getElementById('calcStepLen');
    const calcInitBtn = document.getElementById('calcInitBtn');
    const resetToInitialBtn = document.getElementById('calcResetInitialBtn');
    const moveStepBtn = document.getElementById('calcMoveStepBtn');
    const prevStepBtn = document.getElementById('calcPrevStepBtn');
    const newCalcBtn = document.getElementById('calcNewCalcBtn');
    const fovHSpan = document.getElementById('calcFovH');
    const fovVSpan = document.getElementById('calcFovV');
    const initPxWSpan = document.getElementById('calcInitPxW');
    const initPxHSpan = document.getElementById('calcInitPxH');
    const currentUdisplay = document.getElementById('calcCurrentU');
    const stepCounterSpan = document.getElementById('calcStepCounter');
    const currPxWSpan = document.getElementById('calcCurrPxW');
    const currPxHSpan = document.getElementById('calcCurrPxH');
    const deltaWSpan = document.getElementById('calcDeltaW');
    const deltaHSpan = document.getElementById('calcDeltaH');
    const ratioWSpan = document.getElementById('calcRatioW');
    const ratioHSpan = document.getElementById('calcRatioH');
    const warningDiv = document.getElementById('calcWarningMsg');

    // 核心状态
    let state = {
      canvasW: 1920, canvasH: 1080, objW: 40, objH: 160, initU: 200, focal: 50,
      currentU: 200, currentX: 0, currentY: 0, initX: 0, initY: 0,
      stepCount: 0, lastX: 0, lastY: 0, historyStack: [],
      filmWide: 36, isInitialized: false
    };

    function showWarning(msg) {
      if (warningDiv) {
        warningDiv.innerText = msg;
        warningDiv.style.display = 'block';
        setTimeout(() => { warningDiv.style.display = 'none'; }, 3000);
      } else { alert(msg); }
    }

    function computeFOVAndPixel(canvasW, canvasH, focalMM, objW_cm, objH_cm, u_cm) {
      const filmWide = 36;
      const filmHigh = (filmWide / canvasW) * canvasH;
      const fovWideRad = 2 * Math.atan(filmWide / (2 * focalMM));
      const fovHighRad = 2 * Math.atan(filmHigh / (2 * focalMM));
      let x_px = 0, y_px = 0;
      if (u_cm > 0 && objW_cm > 0 && objH_cm > 0) {
        x_px = canvasW / fovWideRad * Math.atan(objW_cm / u_cm);
        y_px = canvasH / fovHighRad * Math.atan(objH_cm / u_cm);
      }
      if (isNaN(x_px) || !isFinite(x_px)) x_px = 0;
      if (isNaN(y_px) || !isFinite(y_px)) y_px = 0;
      return {
        fovWideRad, fovHighRad, filmHigh,
        x_px, y_px,
        fovWideDeg: fovWideRad * 180 / Math.PI,
        fovHighDeg: fovHighRad * 180 / Math.PI
      };
    }

    function pushToHistory() {
      if (!state.isInitialized) return;
      state.historyStack.push({
        currentU: state.currentU, currentX: state.currentX, currentY: state.currentY,
        stepCount: state.stepCount, lastX: state.lastX, lastY: state.lastY
      });
      if (state.historyStack.length > 50) state.historyStack.shift();
    }

    function popHistory() {
      if (!state.isInitialized || state.historyStack.length === 0) return false;
      const prev = state.historyStack.pop();
      state.currentU = prev.currentU;
      state.currentX = prev.currentX;
      state.currentY = prev.currentY;
      state.stepCount = prev.stepCount;
      state.lastX = prev.lastX;
      state.lastY = prev.lastY;
      refreshDisplay();
      return true;
    }

    function refreshDisplay() {
      const { fovWideDeg, fovHighDeg } = computeFOVAndPixel(
        state.canvasW, state.canvasH, state.focal, state.objW, state.objH, state.currentU
      );
      if (state.isInitialized) {
        fovHSpan.innerText = fovWideDeg.toFixed(2) + '°';
        fovVSpan.innerText = fovHighDeg.toFixed(2) + '°';
        initPxWSpan.innerText = state.initX.toFixed(2);
        initPxHSpan.innerText = state.initY.toFixed(2);
        currentUdisplay.innerText = state.currentU.toFixed(2) + ' cm';
        currPxWSpan.innerText = state.currentX.toFixed(2);
        currPxHSpan.innerText = state.currentY.toFixed(2);
      } else {
        fovHSpan.innerText = '—'; fovVSpan.innerText = '—';
        initPxWSpan.innerText = '—'; initPxHSpan.innerText = '—';
        currentUdisplay.innerText = '—';
        currPxWSpan.innerText = '—'; currPxHSpan.innerText = '—';
      }
      if (state.isInitialized && state.stepCount > 0) {
        const deltaX = state.currentX - state.lastX;
        const deltaY = state.currentY - state.lastY;
        deltaWSpan.innerText = (deltaX >= 0 ? '+' : '') + deltaX.toFixed(2);
        deltaHSpan.innerText = (deltaY >= 0 ? '+' : '') + deltaY.toFixed(2);
        if (state.initX !== 0) ratioWSpan.innerText = (state.currentX / state.initX * 100).toFixed(2) + '%';
        else ratioWSpan.innerText = '—';
        if (state.initY !== 0) ratioHSpan.innerText = (state.currentY / state.initY * 100).toFixed(2) + '%';
        else ratioHSpan.innerText = '—';
      } else if (state.isInitialized && state.stepCount === 0) {
        deltaWSpan.innerText = '0.00'; deltaHSpan.innerText = '0.00';
        ratioWSpan.innerText = '100.00%'; ratioHSpan.innerText = '100.00%';
      } else {
        deltaWSpan.innerText = '—'; deltaHSpan.innerText = '—';
        ratioWSpan.innerText = '—'; ratioHSpan.innerText = '—';
      }
      stepCounterSpan.innerText = state.stepCount;
    }

    function initializeFromInputs(resetStep = true) {
      let canvasW = parseFloat(canvasWInput.value);
      let canvasH = parseFloat(canvasHInput.value);
      let objW = parseFloat(objWInput.value);
      let objH = parseFloat(objHInput.value);
      let u = parseFloat(distanceInput.value);
      let focal = parseFloat(focalInput.value);
      if (isNaN(canvasW) || canvasW <= 0) { showWarning('画布宽度必须为正数'); return false; }
      if (isNaN(canvasH) || canvasH <= 0) { showWarning('画布高度必须为正数'); return false; }
      if (isNaN(objW) || objW <= 0) { showWarning('物体宽度必须 > 0'); return false; }
      if (isNaN(objH) || objH <= 0) { showWarning('物体高度必须 > 0'); return false; }
      if (isNaN(u) || u <= 0) { showWarning('物距必须大于0 cm'); return false; }
      if (isNaN(focal) || focal <= 0) { showWarning('焦距必须为正数(mm)'); return false; }
      state.canvasW = canvasW; state.canvasH = canvasH; state.objW = objW; state.objH = objH;
      state.initU = u; state.focal = focal; state.currentU = u;
      const { x_px, y_px } = computeFOVAndPixel(state.canvasW, state.canvasH, state.focal, state.objW, state.objH, state.currentU);
      state.initX = x_px; state.initY = y_px;
      state.currentX = x_px; state.currentY = y_px;
      state.lastX = x_px; state.lastY = y_px;
      if (resetStep) { state.stepCount = 0; state.historyStack = []; }
      state.isInitialized = true;
      refreshDisplay();
      return true;
    }

    function moveOneStep() {
      if (!state.isInitialized) { showWarning('请先点击【计算初始参数】'); return false; }
      let step = parseFloat(stepLenInput.value);
      if (isNaN(step)) { showWarning('步长必须是数字'); return false; }
      let newU = state.currentU - step;
      if (newU <= 0) { showWarning(`移动后物距 ≤ 0，移动无效。`); return false; }
      pushToHistory();
      const prevX = state.currentX, prevY = state.currentY;
      state.currentU = newU;
      const { x_px, y_px } = computeFOVAndPixel(state.canvasW, state.canvasH, state.focal, state.objW, state.objH, state.currentU);
      state.currentX = x_px; state.currentY = y_px;
      state.lastX = prevX; state.lastY = prevY;
      state.stepCount++;
      refreshDisplay();
      return true;
    }

    function undoStep() {
      if (!state.isInitialized) { showWarning('请先初始化参数'); return false; }
      if (state.stepCount === 0 || state.historyStack.length === 0) { showWarning('没有上一步记录'); return false; }
      popHistory();
      return true;
    }

    function resetToInitial() {
      if (!state.isInitialized) { showWarning('请先计算初始参数'); return; }
      state.currentU = state.initU;
      const { x_px, y_px } = computeFOVAndPixel(state.canvasW, state.canvasH, state.focal, state.objW, state.objH, state.currentU);
      state.currentX = x_px; state.currentY = y_px;
      state.lastX = x_px; state.lastY = y_px;
      state.stepCount = 0;
      state.historyStack = [];
      refreshDisplay();
      showWarning('已重置到初始物距');
    }

    function newCalculation() {
      state.isInitialized = false;
      state.stepCount = 0; state.historyStack = [];
      state.currentX = 0; state.currentY = 0; state.initX = 0; state.initY = 0;
      state.lastX = 0; state.lastY = 0;
      refreshDisplay();
      showWarning('已清空结果，请点击“计算初始参数”');
    }

    // 绑定事件
    if (calcInitBtn) calcInitBtn.onclick = () => { if(initializeFromInputs(true)) showWarning('参数已加载'); };
    if (resetToInitialBtn) resetToInitialBtn.onclick = resetToInitial;
    if (moveStepBtn) moveStepBtn.onclick = moveOneStep;
    if (prevStepBtn) prevStepBtn.onclick = undoStep;
    if (newCalcBtn) newCalcBtn.onclick = newCalculation;

    // 自动初始化一次，展示默认值
    window.addEventListener('load', () => {
      // 确保默认输入框值与state同步（因为HTML中已有value属性）
      if (canvasWInput) canvasWInput.value = '1920';
      if (canvasHInput) canvasHInput.value = '1080';
      if (objWInput) objWInput.value = '40';
      if (objHInput) objHInput.value = '160';
      if (distanceInput) distanceInput.value = '200';
      if (focalInput) focalInput.value = '50';
      if (stepLenInput) stepLenInput.value = '-60';
      initializeFromInputs(true);
    });
  })();
</script>
