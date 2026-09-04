```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PaperBridge — Turn confusing forms into conversations</title>
<style>
  :root {
    --bg: #0f1115;
    --card: #171a21;
    --border: #2a2e38;
    --text: #e8e9ed;
    --muted: #8b8f9c;
    --accent: #4f8cff;
    --accent-soft: rgba(79,140,255,0.15);
    --success: #3ecf8e;
    --success-soft: rgba(62,207,142,0.15);
    --warn: #f5a623;
  }
  * { box-sizing: border-box; }
  body {
    margin: 0;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    background: var(--bg);
    color: var(--text);
    padding: 20px 16px 60px;
    max-width: 480px;
    margin: 0 auto;
  }
  h1 { font-size: 20px; margin: 0 0 4px; }
  .tagline { color: var(--muted); font-size: 13px; margin: 0 0 20px; }
  .card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 16px;
    margin-bottom: 16px;
  }
  .card h2 { font-size: 14px; margin: 0 0 12px; color: var(--muted); text-transform: uppercase; letter-spacing: 0.5px; }
  .field-row {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 12px;
    border-radius: 8px;
    margin-bottom: 6px;
    background: transparent;
    border: 1px solid transparent;
    transition: all 0.4s ease;
  }
  .field-row .label { color: var(--muted); font-size: 13px; }
  .field-row .value { font-size: 14px; font-weight: 500; }
  .field-row.empty .value { color: var(--muted); font-style: italic; }
  .field-row.active {
    background: var(--accent-soft);
    border-color: var(--accent);
    box-shadow: 0 0 0 2px var(--accent-soft);
  }
  .field-row.filled {
    background: rgba(62,207,142,0.08);
  }
  #status {
    font-size: 13px;
    color: var(--muted);
    margin-bottom: 12px;
    min-height: 18px;
  }
  #status.ok { color: var(--success); }
  #status.err { color: #ff6b6b; }
  .log {
    font-family: "SF Mono", Consolas, monospace;
    font-size: 12px;
    color: var(--muted);
    max-height: 180px;
    overflow-y: auto;
  }
  .log-line { padding: 4px 0; border-bottom: 1px solid var(--border); }
  .log-line:last-child { border-bottom: none; }
  .log-line .t { color: var(--accent); margin-right: 6px; }
  .approval-box {
    display: none;
    text-align: center;
  }
  .approval-box.show { display: block; }
  .approval-box p { font-size: 14px; margin: 0 0 14px; }
  .btn-row { display: flex; gap: 10px; justify-content: center; }
  button {
    border: none;
    border-radius: 8px;
    padding: 10px 20px;
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
  }
  .btn-yes { background: var(--success); color: #0f1115; }
  .btn-no { background: var(--border); color: var(--text); }
  .done-badge {
    display: none;
    text-align: center;
    color: var(--success);
    font-weight: 600;
    padding: 10px;
  }
  .done-badge.show { display: block; }
  .missing-badge {
    display: none;
    color: var(--warn);
    font-size: 13px;
    text-align: center;
  }
  .missing-badge.show { display: block; }

  @media (min-width: 768px) {
    body { max-width: min(1400px, 94vw); padding: 32px 40px 70px; }
    h1 { font-size: 26px; }
    .tagline { font-size: 15px; }
    .card { padding: 22px; }
  }

  /* History drawer */
  .hamburger {
    position: fixed;
    top: 16px;
    right: 16px;
    z-index: 20;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    width: 36px;
    height: 36px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    font-size: 18px;
  }
  .drawer-overlay {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.5);
    z-index: 25;
  }
  .drawer-overlay.show { display: block; }
  .drawer {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    width: 78%;
    max-width: 320px;
    background: var(--card);
    border-left: 1px solid var(--border);
    z-index: 30;
    transform: translateX(100%);
    transition: transform 0.25s ease;
    padding: 16px;
    overflow-y: auto;
  }
  .drawer.show { transform: translateX(0); }
  .drawer h2 { font-size: 15px; margin: 0 0 12px; }
  .drawer-search {
    width: 100%;
    padding: 8px 10px;
    border-radius: 8px;
    border: 1px solid var(--border);
    background: var(--bg);
    color: var(--text);
    font-size: 13px;
    margin-bottom: 12px;
  }
  .history-item {
    padding: 10px;
    border-radius: 8px;
    border: 1px solid var(--border);
    margin-bottom: 8px;
    cursor: pointer;
  }
  .history-item:active { background: var(--accent-soft); }
  .history-item .hname { font-size: 13px; font-weight: 600; }
  .history-item .hmeta { font-size: 11px; color: var(--muted); margin-top: 2px; }
  .history-empty { color: var(--muted); font-size: 13px; font-style: italic; }
  .drawer-close {
    background: var(--border);
    color: var(--text);
    border: none;
    border-radius: 6px;
    padding: 6px 10px;
    font-size: 12px;
    margin-bottom: 14px;
  }
</style>
<script defer src="https://cdnjs.cloudflare.com/ajax/libs/tesseract.js/5.0.4/tesseract.min.js"></script>
</head>
<body>

  <div class="hamburger" onclick="toggleDrawer(true)">☰</div>
  <div class="drawer-overlay" id="drawerOverlay" onclick="toggleDrawer(false)"></div>
  <div class="drawer" id="drawer">
    <button class="drawer-close" onclick="toggleDrawer(false)">✕ Close</button>
    <h2>Past Applications</h2>
    <input type="text" class="drawer-search" id="drawerSearch" placeholder="Search by name..." oninput="renderHistory()">
    <div id="historyList"></div>
  </div>

  <h1>PaperBridge</h1>
  <p class="tagline">Turn confusing forms into conversations.</p>

  <div class="card">
    <h2>Scan a Document (auto-fill)</h2>
    <p style="font-size:12px; color:var(--muted); margin:0 0 10px;">Point your camera at an existing ID — the agent reads it and fills matching fields. The photo itself is never saved or stored.</p>
    <button id="openScannerBtn" onclick="openScanner()" style="background:var(--accent); color:#fff; padding:8px 14px; font-size:12px;">📷 Scan Document</button>
    <span id="scanStatus" style="font-size:12px; color:var(--muted); margin-left:8px;"></span>
  </div>

  <div class="drawer-overlay" id="scannerOverlay" style="display:none;" onclick="closeScanner()"></div>
  <div id="scannerCard" style="display:none; position:fixed; top:50%; left:50%; transform:translate(-50%,-50%); z-index:40; background:var(--card); border:1px solid var(--border); border-radius:16px; padding:16px; width:90%; max-width:420px;">
    <div style="position:relative; border-radius:12px; overflow:hidden; background:#000;">
      <video id="scannerVideo" autoplay playsinline style="width:100%; display:block;"></video>
      <div style="position:absolute; inset:12%; border:3px solid var(--accent); border-radius:12px; pointer-events:none;"></div>
    </div>
    <p style="font-size:12px; color:var(--muted); text-align:center; margin:10px 0;">Align the document inside the frame</p>
    <div class="btn-row">
      <button class="btn-yes" onclick="captureAndScan()">Capture</button>
      <button class="btn-no" onclick="closeScanner()">Cancel</button>
    </div>
  </div>

  <div class="card">
    <h2>Application Status</h2>
    <div id="status">Waiting for agent to start a form...</div>
    <button onclick="resetDemo()" style="margin-top:10px; background:var(--border); color:var(--text); font-size:12px; padding:6px 12px;">Reset</button>
    <button onclick="simulateAgentCall()" style="margin-top:10px; margin-left:8px; background:var(--accent); color:#fff; font-size:12px; padding:6px 12px;">Simulate Agent Call</button>
  </div>

  <div class="card">
    <h2>Application Type</h2>
    <div class="btn-row" style="justify-content:flex-start; gap:8px; flex-wrap:wrap;">
      <button id="typeNewBtn" onclick="setAppType('new_pan')" style="background:var(--accent); color:#fff; padding:8px 14px; font-size:12px;">New PAN</button>
      <button id="typeCorrectionBtn" onclick="setAppType('pan_correction')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">PAN Correction</button>
      <button id="typeVoterBtn" onclick="setAppType('voter_id')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Voter ID</button>
      <button id="typeVoterCorrectionBtn" onclick="setAppType('voter_correction')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Voter ID Correction</button>
      <button id="typeAadhaarApplyBtn" onclick="setAppType('aadhaar_apply')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Aadhaar Apply</button>
      <button id="typeAadhaarCorrectionBtn" onclick="setAppType('aadhaar_correction')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Aadhaar Correction</button>
      <button id="typePassportApplyBtn" onclick="setAppType('passport_apply')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Passport Apply</button>
      <button id="typePassportCorrectionBtn" onclick="setAppType('passport_correction')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Passport Correction</button>
      <button id="typeRationApplyBtn" onclick="setAppType('ration_card_apply')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Ration Card Apply</button>
      <button id="typeRationCorrectionBtn" onclick="setAppType('ration_card_correction')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Ration Card Correction</button>
      <button id="typeAyushmanApplyBtn" onclick="setAppType('ayushman_apply')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Ayushman Apply</button>
      <button id="typeAyushmanCorrectionBtn" onclick="setAppType('ayushman_correction')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Ayushman Correction</button>
      <button id="typeBankBtn" onclick="setAppType('bank_account_apply')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Bank Account</button>
      <button id="typeLicBtn" onclick="setAppType('lic_apply')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">LIC Policy</button>
      <button id="typeDLApplyBtn" onclick="setAppType('driving_license_apply')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Driving License Apply</button>
      <button id="typeDLRenewalBtn" onclick="setAppType('driving_license_renewal')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">DL Renewal</button>
      <button id="typeDLCorrectionBtn" onclick="setAppType('driving_license_correction')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">DL Address Change</button>
      <button id="typeIncomeBtn" onclick="setAppType('income_certificate_apply')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Income Certificate</button>
      <button id="typeBirthBtn" onclick="setAppType('birth_certificate_apply')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Birth Certificate</button>
      <button id="typeDeathBtn" onclick="setAppType('death_certificate_apply')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Death Certificate</button>
      <button id="typeVisaBtn" onclick="setAppType('visa_apply')" style="background:var(--border); color:var(--text); padding:8px 14px; font-size:12px;">Visa Application</button>
    </div>
  </div>

  <div class="card" id="correctionSubTypeCard" style="display:none;">
    <h2>What are you correcting?</h2>
    <div class="btn-row" style="justify-content:flex-start; gap:8px; flex-wrap:wrap;" id="correctionSubTypeButtons"></div>
  </div>

  <div class="card" id="bankNameCard" style="display:none;">
    <h2>Choose Bank</h2>
    <div class="btn-row" style="justify-content:flex-start; gap:8px; flex-wrap:wrap;" id="bankNameButtons"></div>
  </div>

  <div class="card" id="bankAccountTypeCard" style="display:none;">
    <h2>Account Type</h2>
    <div class="btn-row" style="justify-content:flex-start; gap:8px; flex-wrap:wrap;" id="bankAccountTypeButtons"></div>
  </div>

  <div class="card" id="visaCountryCard" style="display:none;">
    <h2>Destination Country</h2>
    <div class="btn-row" style="justify-content:flex-start; gap:8px; flex-wrap:wrap;" id="visaCountryButtons"></div>
  </div>

  <div class="card" id="visaTypeCard" style="display:none;">
    <h2>Visa Type</h2>
    <div class="btn-row" style="justify-content:flex-start; gap:8px; flex-wrap:wrap;" id="visaTypeButtons"></div>
  </div>

  <div class="card" id="licPolicyCard" style="display:none;">
    <h2>Choose LIC Policy</h2>
    <div class="btn-row" style="justify-content:flex-start; gap:8px; flex-wrap:wrap;" id="licPolicyButtons"></div>
  </div>

  <div class="card">
    <h2 id="formTitle">PAN Application — Form 49A</h2>
    <div class="field-row empty" data-field="full_name">
      <span class="label">Full Name</span>
      <span class="value">—</span>
    </div>
    <div class="field-row empty" data-field="father_name">
      <span class="label">Father's Name</span>
      <span class="value">—</span>
    </div>
    <div class="field-row empty" data-field="dob">
      <span class="label">Date of Birth</span>
      <span class="value">—</span>
    </div>
    <div class="field-row empty" data-field="address">
      <span class="label">Address</span>
      <span class="value">—</span>
    </div>
    <div class="field-row empty" data-field="extra1" id="extraRow1" style="display:none;">
      <span class="label" id="extraLabel1">Extra</span>
      <span class="value">—</span>
    </div>
    <div class="field-row empty" data-field="extra2" id="extraRow2" style="display:none;">
      <span class="label" id="extraLabel2">Extra</span>
      <span class="value">—</span>
    </div>
    <div class="field-row empty" data-field="new_value" id="newValueRow" style="display:none;">
      <span class="label" id="newValueLabel">New Value</span>
      <span class="value">—</span>
    </div>
  </div>

  <div class="card">
    <div class="missing-badge" id="missingBadge"></div>
    <div class="approval-box" id="approvalBox">
      <p>All fields filled. Submit this application?</p>
      <div class="btn-row">
        <button class="btn-yes" onclick="humanApprove(true)">Yes, Submit</button>
        <button class="btn-no" onclick="humanApprove(false)">No, Cancel</button>
      </div>
    </div>
    <div class="done-badge" id="doneBadge">✓ Application approved and submitted</div>
  </div>

  <div class="card">
    <h2>Agent Activity Log</h2>
    <div class="log" id="log">
      <div class="log-line" style="color:var(--muted); font-style:italic;">No activity yet.</div>
    </div>
  </div>

<script>
// ---------- State ----------
let state = null; // { form_id, application_type, fields: {}, approved, activity_log: [] }
let currentAppType = 'new_pan';
let currentCorrectionSubType = 'name';
let currentBankName = 'sbi';
let currentBankAccountType = 'savings';
let currentLicPolicyType = 'jeevan_anand';
let currentVisaCountry = 'uae';
let currentVisaType = 'tourist';

// ---------- Central config: add a new application type here and everything else follows ----------
const APPLICATION_TYPES = {
  new_pan:              { label: 'PAN Application — Form 49A', btnId: 'typeNewBtn', kind: 'apply' },
  pan_correction:       { label: 'PAN Correction Request', btnId: 'typeCorrectionBtn', kind: 'correction', idField: 'pan_number', idLabel: 'Existing PAN Number' },
  voter_id:             { label: 'Voter ID Application — Form 6', btnId: 'typeVoterBtn', kind: 'apply' },
  voter_correction:     { label: 'Voter ID Correction — Form 8', btnId: 'typeVoterCorrectionBtn', kind: 'correction', idField: 'voter_id_number', idLabel: 'Existing Voter ID (EPIC) Number' },
  aadhaar_apply:        { label: 'Aadhaar Enrolment', btnId: 'typeAadhaarApplyBtn', kind: 'apply' },
  aadhaar_correction:   { label: 'Aadhaar Correction Request', btnId: 'typeAadhaarCorrectionBtn', kind: 'correction', idField: 'aadhaar_number', idLabel: 'Existing Aadhaar Number' },
  passport_apply:       { label: 'Passport Application', btnId: 'typePassportApplyBtn', kind: 'apply' },
  passport_correction:  { label: 'Passport Correction Request', btnId: 'typePassportCorrectionBtn', kind: 'correction', idField: 'passport_number', idLabel: 'Existing Passport Number', extraSubtypes: { country: 'Country' } },
  ration_card_apply:        { label: 'Ration Card Application', btnId: 'typeRationApplyBtn', kind: 'apply' },
  ration_card_correction:   { label: 'Ration Card Correction', btnId: 'typeRationCorrectionBtn', kind: 'correction', idField: 'ration_card_number', idLabel: 'Existing Ration Card Number' },
  ayushman_apply:            { label: 'Ayushman Bharat Card Application', btnId: 'typeAyushmanApplyBtn', kind: 'apply' },
  ayushman_correction:      { label: 'Ayushman Card Correction', btnId: 'typeAyushmanCorrectionBtn', kind: 'correction', idField: 'ayushman_card_number', idLabel: 'Existing Ayushman Card Number' },
  bank_account_apply:  { label: 'Bank Account Opening', btnId: 'typeBankBtn', kind: 'bank' },
  lic_apply:           { label: 'LIC Policy Application', btnId: 'typeLicBtn', kind: 'lic' },
  driving_license_apply:      { label: 'Driving Licence Application — Form 4', btnId: 'typeDLApplyBtn', kind: 'apply' },
  driving_license_renewal:    { label: 'Driving Licence Renewal — Form 9', btnId: 'typeDLRenewalBtn', kind: 'renewal', idField: 'dl_number', idLabel: 'Existing Driving Licence Number' },
  driving_license_correction: { label: 'Driving Licence Address Change', btnId: 'typeDLCorrectionBtn', kind: 'correction', idField: 'dl_number', idLabel: 'Existing Driving Licence Number' },
  income_certificate_apply:   { label: 'Income Certificate Application', btnId: 'typeIncomeBtn', kind: 'apply' },
  birth_certificate_apply:    { label: 'Birth Certificate Application', btnId: 'typeBirthBtn', kind: 'apply' },
  death_certificate_apply:    { label: 'Death Certificate Application', btnId: 'typeDeathBtn', kind: 'apply' },
  visa_apply:                 { label: 'Visa Application', btnId: 'typeVisaBtn', kind: 'visa' }
};

const COMMON_CORRECTION_FIELDS = {
  name: 'Full Name', address: 'Address', phone: 'Phone Number', email: 'Email ID',
  dob: 'Date of Birth', father_name: "Father's Name", mother_name: "Mother's Name"
};

const NEW_VALUE_LABELS = {
  name: 'New Full Name', address: 'New Address', phone: 'New Phone Number', email: 'New Email ID',
  father_name: "New Father's Name", mother_name: "New Mother's Name",
  country: 'New Country', dob: 'New Date of Birth'
};

// Top 10 most-trusted Indian banks (public + private mix)
const BANK_NAMES = {
  sbi: 'State Bank of India', hdfc: 'HDFC Bank', icici: 'ICICI Bank', axis: 'Axis Bank',
  kotak: 'Kotak Mahindra Bank', pnb: 'Punjab National Bank', bob: 'Bank of Baroda',
  canara: 'Canara Bank', federal: 'Federal Bank', union: 'Union Bank of India'
};

const BANK_ACCOUNT_TYPES = {
  savings: 'Savings Account', current: 'Current Account', salary: 'Salary Account',
  zero_balance: 'Zero Balance (BSBDA)', business: 'Business Account'
};

// Real, commonly-held LIC plans (as of 2026)
const LIC_POLICIES = {
  jeevan_anand: 'New Jeevan Anand (Plan 915)',
  jeevan_labh: 'Jeevan Labh (Plan 936)',
  jeevan_umang: 'Jeevan Umang (Plan 945)',
  jeevan_lakshya: 'Jeevan Lakshya (Plan 933)',
  tech_term: 'Tech-Term (Plan 954)',
  jeevan_amar: 'Jeevan Amar (Plan 955)',
  bima_jyoti: 'Bima Jyoti',
  siip: 'SIIP (ULIP)'
};

// Top 50 visa destination countries for Indian travelers (tourist/business/student/work combined)
const VISA_COUNTRIES = {
  uae: 'United Arab Emirates', saudi: 'Saudi Arabia', usa: 'United States', thailand: 'Thailand',
  singapore: 'Singapore', uk: 'United Kingdom', qatar: 'Qatar', kuwait: 'Kuwait', oman: 'Oman',
  bahrain: 'Bahrain', malaysia: 'Malaysia', indonesia: 'Indonesia', srilanka: 'Sri Lanka',
  bhutan: 'Bhutan', maldives: 'Maldives', mauritius: 'Mauritius', canada: 'Canada',
  australia: 'Australia', germany: 'Germany', france: 'France', ireland: 'Ireland',
  newzealand: 'New Zealand', japan: 'Japan', southkorea: 'South Korea', china: 'China',
  vietnam: 'Vietnam', cambodia: 'Cambodia', philippines: 'Philippines', hongkong: 'Hong Kong',
  turkey: 'Turkey', egypt: 'Egypt', southafrica: 'South Africa', kenya: 'Kenya', italy: 'Italy',
  spain: 'Spain', netherlands: 'Netherlands', switzerland: 'Switzerland', sweden: 'Sweden',
  norway: 'Norway', denmark: 'Denmark', russia: 'Russia', brazil: 'Brazil', mexico: 'Mexico',
  argentina: 'Argentina', israel: 'Israel', jordan: 'Jordan', morocco: 'Morocco',
  seychelles: 'Seychelles', fiji: 'Fiji', cyprus: 'Cyprus', portugal: 'Portugal'
};

const VISA_TYPES = {
  tourist: 'Tourist / Visitor', business: 'Business', student: 'Student', work: 'Work / Employment', transit: 'Transit'
};

function getCorrectionSubtypes(type) {
  const cfg = APPLICATION_TYPES[type];
  if (!cfg || cfg.kind !== 'correction') return {};
  return { ...COMMON_CORRECTION_FIELDS, ...(cfg.extraSubtypes || {}) };
}

function renderButtonList(containerId, optionsMap, currentKey, onClickFn) {
  const container = document.getElementById(containerId);
  container.innerHTML = '';
  Object.entries(optionsMap).forEach(([key, label]) => {
    const btn = document.createElement('button');
    btn.textContent = label;
    btn.dataset.key = key;
    btn.style.padding = '6px 12px';
    btn.style.fontSize = '12px';
    btn.style.background = key === currentKey ? 'var(--accent)' : 'var(--border)';
    btn.style.color = key === currentKey ? '#fff' : 'var(--text)';
    btn.onclick = () => onClickFn(key);
    container.appendChild(btn);
  });
}

function renderCorrectionSubTypeButtons(type) {
  const subtypes = getCorrectionSubtypes(type);
  const keys = Object.keys(subtypes);
  if (!keys.includes(currentCorrectionSubType)) currentCorrectionSubType = keys[0];
  renderButtonList('correctionSubTypeButtons', subtypes, currentCorrectionSubType, setCorrectionSubType);
  document.getElementById('newValueLabel').textContent = NEW_VALUE_LABELS[currentCorrectionSubType] || 'New Value';
}

function resetExtraRow(rowId) {
  const row = document.getElementById(rowId);
  row.classList.remove('active', 'filled');
  row.classList.add('empty');
  row.querySelector('.value').textContent = '—';
}

function setAppType(type) {
  currentAppType = type;
  const cfg = APPLICATION_TYPES[type] || {};

  Object.entries(APPLICATION_TYPES).forEach(([t, c]) => {
    const btn = document.getElementById(c.btnId);
    if (!btn) return;
    btn.style.background = t === type ? 'var(--accent)' : 'var(--border)';
    btn.style.color = t === type ? '#fff' : 'var(--text)';
  });

  document.getElementById('formTitle').textContent = cfg.label || 'Application';

  const isCorrection = cfg.kind === 'correction';
  const isRenewal = cfg.kind === 'renewal';
  const isBank = cfg.kind === 'bank';
  const isLic = cfg.kind === 'lic';
  const isVisa = cfg.kind === 'visa';

  document.getElementById('newValueRow').style.display = isCorrection ? 'flex' : 'none';
  document.getElementById('correctionSubTypeCard').style.display = isCorrection ? 'block' : 'none';
  if (isCorrection) renderCorrectionSubTypeButtons(type);

  document.getElementById('bankNameCard').style.display = isBank ? 'block' : 'none';
  document.getElementById('bankAccountTypeCard').style.display = isBank ? 'block' : 'none';
  if (isBank) {
    renderButtonList('bankNameButtons', BANK_NAMES, currentBankName, setBankName);
    renderButtonList('bankAccountTypeButtons', BANK_ACCOUNT_TYPES, currentBankAccountType, setBankAccountType);
  }

  document.getElementById('licPolicyCard').style.display = isLic ? 'block' : 'none';
  if (isLic) renderButtonList('licPolicyButtons', LIC_POLICIES, currentLicPolicyType, setLicPolicyType);

  document.getElementById('visaCountryCard').style.display = isVisa ? 'block' : 'none';
  document.getElementById('visaTypeCard').style.display = isVisa ? 'block' : 'none';
  if (isVisa) {
    renderButtonList('visaCountryButtons', VISA_COUNTRIES, currentVisaCountry, setVisaCountry);
    renderButtonList('visaTypeButtons', VISA_TYPES, currentVisaType, setVisaType);
  }

  resetExtraRow('extraRow1');
  resetExtraRow('extraRow2');

  if (isCorrection || isRenewal) {
    document.getElementById('extraLabel1').textContent = cfg.idLabel;
    document.getElementById('extraRow1').setAttribute('data-field', cfg.idField);
    document.getElementById('extraRow1').style.display = 'flex';
    document.getElementById('extraRow2').style.display = 'none';
  } else if (isBank) {
    document.getElementById('extraLabel1').textContent = 'Bank Name';
    document.getElementById('extraRow1').setAttribute('data-field', 'bank_name');
    document.getElementById('extraRow1').style.display = 'flex';
    document.getElementById('extraLabel2').textContent = 'Account Type';
    document.getElementById('extraRow2').setAttribute('data-field', 'account_type');
    document.getElementById('extraRow2').style.display = 'flex';
  } else if (isLic) {
    document.getElementById('extraLabel1').textContent = 'Policy';
    document.getElementById('extraRow1').setAttribute('data-field', 'policy_type');
    document.getElementById('extraRow1').style.display = 'flex';
    document.getElementById('extraRow2').style.display = 'none';
  } else if (isVisa) {
    document.getElementById('extraLabel1').textContent = 'Destination Country';
    document.getElementById('extraRow1').setAttribute('data-field', 'destination_country');
    document.getElementById('extraRow1').style.display = 'flex';
    document.getElementById('extraLabel2').textContent = 'Visa Type';
    document.getElementById('extraRow2').setAttribute('data-field', 'visa_type');
    document.getElementById('extraRow2').style.display = 'flex';
  } else {
    document.getElementById('extraRow1').style.display = 'none';
    document.getElementById('extraRow2').style.display = 'none';
  }
}

function setCorrectionSubType(sub) {
  currentCorrectionSubType = sub;
  renderCorrectionSubTypeButtons(currentAppType);
}

function setBankName(key) {
  currentBankName = key;
  renderButtonList('bankNameButtons', BANK_NAMES, currentBankName, setBankName);
}

function setBankAccountType(key) {
  currentBankAccountType = key;
  renderButtonList('bankAccountTypeButtons', BANK_ACCOUNT_TYPES, currentBankAccountType, setBankAccountType);
}

function setLicPolicyType(key) {
  currentLicPolicyType = key;
  renderButtonList('licPolicyButtons', LIC_POLICIES, currentLicPolicyType, setLicPolicyType);
}

function setVisaCountry(key) {
  currentVisaCountry = key;
  renderButtonList('visaCountryButtons', VISA_COUNTRIES, currentVisaCountry, setVisaCountry);
}

function setVisaType(key) {
  currentVisaType = key;
  renderButtonList('visaTypeButtons', VISA_TYPES, currentVisaType, setVisaType);
}

function nowStr() {
  const d = new Date();
  return d.toTimeString().slice(0,5);
}

function log(msg) {
  const el = document.getElementById('log');
  if (el.children.length === 1 && el.children[0].textContent === 'No activity yet.') {
    el.innerHTML = '';
  }
  const line = document.createElement('div');
  line.className = 'log-line';
  line.innerHTML = `<span class="t">${nowStr()}</span>${msg}`;
  el.prepend(line);
  if (state) {
    state.activity_log.push({ time: nowStr(), action: msg });
    localStorage.setItem('paperbridge_state', JSON.stringify(state));
    saveToHistory();
  }
}

function setStatus(msg, kind) {
  const el = document.getElementById('status');
  el.textContent = msg;
  el.className = kind || '';
}

function highlightField(fieldName, value) {
  const row = document.querySelector(`.field-row[data-field="${fieldName}"]`);
  if (!row) return;
  row.querySelector('.value').textContent = value;
  row.classList.remove('empty');
  row.classList.add('active');
  setTimeout(() => {
    row.classList.remove('active');
    row.classList.add('filled');
  }, 600);
}

// ---------- WebMCP Tool Registration ----------
let registeredTools = {};

function registerTools() {
  const toolDefs = [
    {
      name: "start_form",
      description: "Initializes a new PAN application form session. Call this first before filling any fields.",
      inputSchema: {
        type: "object",
        properties: {
          application_type: { type: "string", enum: ["new_pan", "pan_correction", "voter_id", "voter_correction", "aadhaar_apply", "aadhaar_correction", "passport_apply", "passport_correction", "ration_card_apply", "ration_card_correction", "ayushman_apply", "ayushman_correction", "bank_account_apply", "lic_apply", "driving_license_apply", "driving_license_renewal", "driving_license_correction", "income_certificate_apply", "birth_certificate_apply", "death_certificate_apply", "visa_apply"] }
        },
        required: ["application_type"]
      },
      execute: async (input) => {
        const form_id = "form_" + Math.random().toString(36).slice(2, 8);
        state = {
          form_id,
          application_type: input.application_type,
          fields: { full_name: "", father_name: "", dob: "", address: "", pan_number: "", aadhaar_number: "", passport_number: "", voter_id_number: "", ration_card_number: "", ayushman_card_number: "", bank_name: "", account_type: "", policy_type: "", dl_number: "", destination_country: "", visa_type: "", new_value: "" },
          approved: false,
          activity_log: []
        };
        localStorage.setItem('paperbridge_state', JSON.stringify(state));
        log(`start_form called → ${form_id} (${input.application_type})`);
        setStatus(`Form started: ${form_id}`, 'ok');
        return {
          content: [{ type: "text", text: JSON.stringify({ form_id }) }],
          structuredContent: { form_id }
        };
      }
    },
    {
      name: "fill_field",
      description: "Fills one field on the active PAN application form.",
      inputSchema: {
        type: "object",
        properties: {
          form_id: { type: "string" },
          field_name: { type: "string", enum: ["full_name", "father_name", "dob", "address", "pan_number", "aadhaar_number", "passport_number", "voter_id_number", "ration_card_number", "ayushman_card_number", "bank_name", "account_type", "policy_type", "dl_number", "destination_country", "visa_type", "new_value"] },
          value: { type: "string" }
        },
        required: ["form_id", "field_name", "value"]
      },
      execute: async (input) => {
        if (!state || state.form_id !== input.form_id) {
          log(`fill_field FAILED — no active form matching ${input.form_id}`);
          return { content: [{ type: "text", text: "Error: no active form. Call start_form first." }] };
        }
        state.fields[input.field_name] = input.value;
        localStorage.setItem('paperbridge_state', JSON.stringify(state));
        highlightField(input.field_name, input.value);
        log(`fill_field → ${input.field_name} = "${input.value}"`);
        return {
          content: [{ type: "text", text: JSON.stringify({ field_name: input.field_name, status: "filled" }) }],
          structuredContent: { field_name: input.field_name, status: "filled" }
        };
      }
    },
    {
      name: "validate_form",
      description: "Checks all required fields are filled and requests human approval before submission.",
      inputSchema: {
        type: "object",
        properties: { form_id: { type: "string" } },
        required: ["form_id"]
      },
      execute: async (input) => {
        if (!state || state.form_id !== input.form_id) {
          return { content: [{ type: "text", text: "Error: no active form." }] };
        }
        const BASE_FIELDS = ['full_name', 'father_name', 'dob', 'address'];
        const cfg = APPLICATION_TYPES[state.application_type] || {};
        let requiredFields = [...BASE_FIELDS];
        if (cfg.kind === 'correction') requiredFields.push(cfg.idField, 'new_value');
        else if (cfg.kind === 'renewal') requiredFields.push(cfg.idField);
        else if (cfg.kind === 'bank') requiredFields.push('bank_name', 'account_type');
        else if (cfg.kind === 'lic') requiredFields.push('policy_type');
        else if (cfg.kind === 'visa') requiredFields.push('destination_country', 'visa_type');
        const missing = requiredFields.filter(k => !state.fields[k] || state.fields[k].trim() === "");

        log(`validate_form called → ${missing.length === 0 ? "all fields complete" : missing.length + " field(s) missing"}`);

        if (missing.length > 0) {
          document.getElementById('missingBadge').textContent = "Missing: " + missing.join(", ");
          document.getElementById('missingBadge').classList.add('show');
          setStatus('Validation failed — missing fields', 'err');
          return {
            content: [{ type: "text", text: JSON.stringify({ ready_for_approval: false, missing_fields: missing }) }],
            structuredContent: { form_id: input.form_id, ready_for_approval: false, missing_fields: missing }
          };
        }

        document.getElementById('missingBadge').classList.remove('show');
        document.getElementById('approvalBox').classList.add('show');
        setStatus('Waiting for human approval...', 'ok');
        return {
          content: [{ type: "text", text: JSON.stringify({ ready_for_approval: true, missing_fields: [] }) }],
          structuredContent: { form_id: input.form_id, ready_for_approval: true, missing_fields: [] }
        };
      }
    },
    {
      name: "scan_document",
      description: "Extracts identity fields (name, DOB, PAN, Aadhaar number) from OCR text already read off a photographed ID document, and fills matching fields on the active form. The photo itself is never stored — only the extracted text is passed in.",
      inputSchema: {
        type: "object",
        properties: {
          form_id: { type: "string" },
          extracted_text: { type: "string", description: "OCR text already extracted from the document image" }
        },
        required: ["form_id", "extracted_text"]
      },
      execute: async (input) => {
        if (!state || state.form_id !== input.form_id) {
          return { content: [{ type: "text", text: "Error: no active form." }] };
        }
        const extracted = extractFieldsFromText(input.extracted_text);
        const filled = [];
        for (const [fieldName, value] of Object.entries(extracted)) {
          if (!(fieldName in state.fields)) continue;
          state.fields[fieldName] = value;
          highlightField(fieldName, value);
          filled.push(fieldName);
        }
        localStorage.setItem('paperbridge_state', JSON.stringify(state));
        log(`scan_document → auto-filled ${filled.length} field(s): ${filled.join(', ') || 'none'}`);
        return {
          content: [{ type: "text", text: JSON.stringify({ filled_fields: filled }) }],
          structuredContent: { form_id: input.form_id, filled_fields: filled }
        };
      }
    }
  ];

  // Always keep a local reference so the on-page "Simulate" button works
  // regardless of whether the browser exposes document.modelContext.
  toolDefs.forEach(t => { registeredTools[t.name] = t; });

  if (!document.modelContext) {
    setStatus('document.modelContext NOT found on this browser/agent environment. (Tool logic still available via "Simulate Agent Call" below.)', 'err');
    return false;
  }

  toolDefs.forEach(t => document.modelContext.registerTool(t));
  return true;
}

// ---------- Human approval (manual, not agent-callable) ----------
function humanApprove(yes) {
  document.getElementById('approvalBox').classList.remove('show');
  if (yes) {
    state.approved = true;
    localStorage.setItem('paperbridge_state', JSON.stringify(state));
    log('Human approved — application submitted');
    document.getElementById('doneBadge').classList.add('show');
    setStatus('Approved & submitted.', 'ok');
  } else {
    log('Human declined — application not submitted');
    setStatus('Declined by human.', 'err');
  }
}

// ---------- Document Scan (live camera OCR — image is never saved anywhere) ----------
let scannerStream = null;

function extractFieldsFromText(text) {
  const extracted = {};
  let remaining = text.replace(/\s+/g, ' ');

  const dobMatch = remaining.match(/\b\d{2}[\/\-]\d{2}[\/\-]\d{4}\b/);
  if (dobMatch) { extracted.dob = dobMatch[0]; remaining = remaining.replace(dobMatch[0], ' '); }

  const panMatch = remaining.match(/\b[A-Z]{5}[0-9]{4}[A-Z]\b/);
  if (panMatch) { extracted.pan_number = panMatch[0]; remaining = remaining.replace(panMatch[0], ' '); }

  const aadhaarMatch = remaining.match(/\b\d{4}\s?\d{4}\s?\d{4}\b/);
  if (aadhaarMatch) { extracted.aadhaar_number = aadhaarMatch[0].replace(/\s/g, ''); remaining = remaining.replace(aadhaarMatch[0], ' '); }

  const stopWords = 'DOB|Date|Father|S\\/O|D\\/O|Address|Permanent';
  const wordPattern = `(?:(?!${stopWords})[A-Z][A-Za-z]*)`;
  const nameMatch = remaining.match(new RegExp(`\\bName[:\\s]+(${wordPattern}(?:\\s${wordPattern}){0,3})`));
  if (nameMatch) extracted.full_name = nameMatch[1].trim();

  const fatherMatch = remaining.match(new RegExp(`(?:Father'?s?\\s*Name|S\\/O|D\\/O)[:\\s]+(${wordPattern}(?:\\s${wordPattern}){0,3})`, 'i'));
  if (fatherMatch) extracted.father_name = fatherMatch[1].trim();

  return extracted;
}

async function openScanner() {
  const statusEl = document.getElementById('scanStatus');
  try {
    scannerStream = await navigator.mediaDevices.getUserMedia({ video: { facingMode: 'environment' } });
    document.getElementById('scannerVideo').srcObject = scannerStream;
    document.getElementById('scannerCard').style.display = 'block';
    document.getElementById('scannerOverlay').style.display = 'block';
    statusEl.textContent = '';
  } catch (err) {
    statusEl.textContent = 'Camera access denied or unavailable.';
  }
}

function closeScanner() {
  if (scannerStream) {
    scannerStream.getTracks().forEach(track => track.stop());
    scannerStream = null;
  }
  document.getElementById('scannerCard').style.display = 'none';
  document.getElementById('scannerOverlay').style.display = 'none';
}

async function captureAndScan() {
  const statusEl = document.getElementById('scanStatus');
  const video = document.getElementById('scannerVideo');

  // Draw the current frame to an in-memory canvas only — this canvas is never
  // appended to the page, never written to state or localStorage, and goes out
  // of scope (garbage collected) as soon as this function finishes.
  const canvas = document.createElement('canvas');
  canvas.width = video.videoWidth;
  canvas.height = video.videoHeight;
  canvas.getContext('2d').drawImage(video, 0, 0);

  closeScanner(); // turn camera off immediately after capture

  if (typeof Tesseract === 'undefined') {
    statusEl.textContent = 'OCR library failed to load — check internet connection.';
    return;
  }

  statusEl.textContent = 'Reading document...';
  try {
    const result = await Tesseract.recognize(canvas, 'eng');
    const extracted = extractFieldsFromText(result.data.text);
    const foundCount = Object.keys(extracted).length;

    if (foundCount === 0) {
      statusEl.textContent = 'No recognizable fields found — try again or fill manually.';
      return;
    }

    if (!state) {
      await registeredTools.start_form.execute({ application_type: currentAppType });
    }

    let filledCount = 0;
    for (const [fieldName, value] of Object.entries(extracted)) {
      if (!(fieldName in state.fields)) continue;
      await registeredTools.fill_field.execute({ form_id: state.form_id, field_name: fieldName, value: value });
      filledCount++;
    }
    statusEl.textContent = `Auto-filled ${filledCount} field(s) from scan. Review before approving.`;
  } catch (err) {
    statusEl.textContent = 'Scan failed — please try again or fill manually.';
  }
  // canvas goes out of scope here — nothing retained anywhere.
}

// ---------- Simulate (for demo/video purposes — manually invokes the same tool functions) ----------
async function simulateAgentCall() {
  const startBtn = document.querySelector('button[onclick="simulateAgentCall()"]');
  startBtn.disabled = true;
  startBtn.textContent = "Running...";

  const tools = registeredTools; // captured at registration time
  const wait = (ms) => new Promise(r => setTimeout(r, ms));

  const r1 = await tools.start_form.execute({ application_type: currentAppType });
  const form_id = JSON.parse(r1.content[0].text).form_id;
  await wait(500);

  const baseFields = {
    full_name: "Ranjan Gogoi",
    father_name: "Deben Gogoi",
    dob: "2008-03-15",
    address: "Assam, India"
  };

  const newValueByType = {
    name: "Ranjan Kumar Gogoi",
    address: "New Address, Assam, India",
    phone: "9435xxxxxx",
    email: "ranjan@example.com",
    father_name: "Deben Gogoi",
    mother_name: "Anima Gogoi",
    country: "India",
    dob: "2008-03-15"
  };

  const cfg = APPLICATION_TYPES[currentAppType] || {};
  let demoFields = baseFields;
  if (cfg.kind === 'correction') {
    demoFields = { ...baseFields, [cfg.idField]: "DEMO-ID-1234", new_value: newValueByType[currentCorrectionSubType] };
  } else if (cfg.kind === 'renewal') {
    demoFields = { ...baseFields, [cfg.idField]: "DEMO-ID-1234" };
  } else if (cfg.kind === 'bank') {
    demoFields = { ...baseFields, bank_name: BANK_NAMES[currentBankName], account_type: BANK_ACCOUNT_TYPES[currentBankAccountType] };
  } else if (cfg.kind === 'lic') {
    demoFields = { ...baseFields, policy_type: LIC_POLICIES[currentLicPolicyType] };
  } else if (cfg.kind === 'visa') {
    demoFields = { ...baseFields, destination_country: VISA_COUNTRIES[currentVisaCountry], visa_type: VISA_TYPES[currentVisaType] };
  }

  for (const [k, v] of Object.entries(demoFields)) {
    await tools.fill_field.execute({ form_id, field_name: k, value: v });
    await wait(600);
  }

  await tools.validate_form.execute({ form_id });
  startBtn.disabled = false;
  startBtn.textContent = "Simulate Agent Call";
}

// ---------- History Drawer ----------
function toggleDrawer(show) {
  document.getElementById('drawer').classList.toggle('show', show);
  document.getElementById('drawerOverlay').classList.toggle('show', show);
  if (show) renderHistory();
}

function getAllForms() {
  try {
    return JSON.parse(localStorage.getItem('paperbridge_all_forms') || '[]');
  } catch (e) { return []; }
}

function saveToHistory() {
  if (!state) return;
  let all = getAllForms();
  const idx = all.findIndex(f => f.form_id === state.form_id);
  const entry = { ...state, saved_at: new Date().toISOString() };
  if (idx >= 0) all[idx] = entry; else all.unshift(entry);
  localStorage.setItem('paperbridge_all_forms', JSON.stringify(all));
}

function renderHistory() {
  const q = (document.getElementById('drawerSearch').value || '').toLowerCase().trim();
  const all = getAllForms();
  const filtered = q
    ? all.filter(f => (f.fields.full_name || '').toLowerCase().includes(q))
    : all;

  const container = document.getElementById('historyList');
  if (filtered.length === 0) {
    container.innerHTML = '<div class="history-empty">No saved applications yet.</div>';
    return;
  }
  container.innerHTML = filtered.map((f, i) => {
    const name = f.fields.full_name || '(no name yet)';
    const status = f.approved ? 'Approved' : 'In progress';
    const d = new Date(f.saved_at);
    const when = d.toLocaleDateString() + ' ' + d.toTimeString().slice(0,5);
    return `<div class="history-item" onclick="loadHistoryItem('${f.form_id}')">
      <div class="hname">${name}</div>
      <div class="hmeta">${status} · ${when} · ${f.form_id}</div>
    </div>`;
  }).join('');
}

function loadHistoryItem(form_id) {
  const all = getAllForms();
  const found = all.find(f => f.form_id === form_id);
  if (!found) return;
  state = JSON.parse(JSON.stringify(found));
  localStorage.setItem('paperbridge_state', JSON.stringify(state));
  setAppType(state.application_type || 'new_pan');

  // Re-render fields
  Object.entries(state.fields).forEach(([k, v]) => {
    const row = document.querySelector(`.field-row[data-field="${k}"]`);
    if (!row) return;
    row.querySelector('.value').textContent = v || '—';
    row.classList.remove('empty', 'active');
    row.classList.toggle('filled', !!v);
  });

  // Re-render log
  const logEl = document.getElementById('log');
  logEl.innerHTML = state.activity_log.length
    ? state.activity_log.slice().reverse().map(l => `<div class="log-line"><span class="t">${l.time}</span>${l.action}</div>`).join('')
    : '<div class="log-line" style="color:var(--muted); font-style:italic;">No activity yet.</div>';

  // Re-render approval/done state
  document.getElementById('approvalBox').classList.remove('show');
  document.getElementById('doneBadge').classList.toggle('show', !!state.approved);
  document.getElementById('missingBadge').classList.remove('show');

  const missing = Object.values(state.fields).some(v => !v);
  if (!state.approved && !missing) {
    document.getElementById('approvalBox').classList.add('show');
  }

  setStatus(`Loaded application: ${state.fields.full_name || state.form_id}`, 'ok');
  toggleDrawer(false);
}

// ---------- Reset ----------
function resetDemo() {
  localStorage.removeItem('paperbridge_state');
  location.reload();
}

// ---------- Init ----------
window.addEventListener('DOMContentLoaded', () => {
  setAppType('new_pan');
  const ok = registerTools();
  if (ok) {
    setStatus('Tools registered. Ready — tell the agent your goal (e.g. "Help me fill a new PAN application for <name>...").', 'ok');
  }
});
</script>
</body>
</html>

```
