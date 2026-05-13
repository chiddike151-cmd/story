import { useState, useRef, useCallback, useEffect } from "react";

// ─────────────────────────────────────────────
// THEME
// ─────────────────────────────────────────────
const T = {
  // sidebar / chrome
  sidebarBg:   "#fdf0f6",
  sidebarBorder: "#f0c8de",
  topbarBg:    "#fff5fa",
  topbarBorder: "#f5c0d8",
  // document canvas
  pageBg:      "#ffffff",
  pageShad:    "0 2px 16px rgba(220,120,170,0.13), 0 1px 3px rgba(200,100,150,0.08)",
  appBg:       "#fce8f3",
  // pinks
  primary:     "#e8337a",
  primaryHov:  "#c8205e",
  primaryPale: "#fde8f2",
  pinkMid:     "#f06090",
  pinkLight:   "#f9c0d8",
  pinkFaint:   "#feeaf4",
  lilac:       "#c880e8",
  // text
  textDark:    "#3a0a28",
  textMid:     "#8a3a60",
  textSoft:    "#b87898",
  textFaint:   "#d8a8c0",
  // toolbar
  toolbarBg:   "#fff8fb",
  toolbarBorder:"#f0c0d8",
};

const F = {
  ui:      "'DM Sans', sans-serif",
  display: "'Playfair Display', Georgia, serif",
  mono:    "Georgia, serif",
};

// ─────────────────────────────────────────────
// HELPERS
// ─────────────────────────────────────────────
const genId = () => Math.random().toString(36).slice(2, 10);

const fmtDate = (ts) =>
  new Date(ts).toLocaleDateString("en-US", { month: "short", day: "numeric", year: "numeric" });

const wordCount = (txt) =>
  txt?.trim() ? txt.trim().split(/\s+/).length : 0;

// ─────────────────────────────────────────────
// PDF EXPORT
// ─────────────────────────────────────────────
function exportPDF(story) {
  const esc = (s = "") => s.replace(/</g, "&lt;").replace(/>/g, "&gt;");
  const body = esc(story.content)
    .replace(/\n\n+/g, "</p><p>")
    .replace(/\n/g, "<br/>");
  const coverStyle = story.cover
    ? `background:url('${story.cover}') center/cover;`
    : `background:linear-gradient(135deg,#f9a8d4,#e879f9,#818cf8);`;

  const w = window.open("", "_blank");
  w.document.write(`<!DOCTYPE html><html><head><meta charset="utf-8"/>
  <title>${esc(story.title)}</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Lora:ital,wght@0,400;1,400&display=swap" rel="stylesheet"/>
  <style>
    *{margin:0;padding:0;box-sizing:border-box} @page{size:A4;margin:0}
    body{font-family:'Lora',Georgia,serif;background:#fff}
    .cover{width:210mm;height:297mm;${coverStyle}display:flex;flex-direction:column;
      align-items:center;justify-content:center;position:relative;page-break-after:always}
    .overlay{position:absolute;inset:0;background:linear-gradient(to bottom,
      rgba(240,80,140,.25) 0%,rgba(180,30,100,.6) 100%)}
    .cc{position:relative;z-index:2;text-align:center;padding:20mm 20mm;color:#fff}
    .ct{font-family:'Playfair Display',serif;font-size:46pt;font-weight:700;
      line-height:1.1;margin-bottom:8mm;text-shadow:0 2px 20px rgba(0,0,0,.4)}
    .rule{width:48mm;height:2pt;background:rgba(255,255,255,.55);border-radius:2pt;margin:0 auto 8mm}
    .ca{font-family:'Lora',serif;font-style:italic;font-size:16pt;opacity:.9}
    .cd{font-size:10pt;opacity:.55;margin-top:6mm;letter-spacing:.1em}
    .page{width:210mm;min-height:297mm;padding:24mm 30mm;background:#fff}
    .ptitle{font-family:'Playfair Display',serif;font-size:28pt;color:#c01860;
      margin-bottom:10mm;padding-bottom:5mm;border-bottom:1.5pt solid #f9c0d8;line-height:1.2}
    .pbody{font-family:'Lora',serif;font-size:12pt;line-height:2;color:#3a0a28}
    .pbody p{margin-bottom:5mm;text-indent:7mm} .pbody p:first-child{text-indent:0}
    .footer{margin-top:14mm;padding-top:4mm;border-top:1pt solid #f9c0d8;
      text-align:center;font-size:9pt;color:#c878a0;font-style:italic}
  </style></head><body>
  <div class="cover"><div class="overlay"></div><div class="cc">
    <div class="ct">${esc(story.title) || "My Story"}</div><div class="rule"></div>
    ${story.author ? `<div class="ca">by ${esc(story.author)}</div>` : ""}
    <div class="cd">${fmtDate(story.createdAt)}</div>
  </div></div>
  <div class="page">
    <div class="ptitle">${esc(story.title) || "My Story"}</div>
    <div class="pbody"><p>${body || "This story is just beginning…"}</p></div>
    <div class="footer">♡ ${esc(story.title)} · ${fmtDate(story.createdAt)} ♡</div>
  </div>
  <script>window.onload=()=>{window.print();setTimeout(()=>window.close(),900)}<\/script>
  </body></html>`);
  w.document.close();
}

// ─────────────────────────────────────────────
// ICON BUTTON (toolbar)
// ─────────────────────────────────────────────
function IconBtn({ label, icon, onClick, active, disabled, wide }) {
  const [hov, setHov] = useState(false);
  return (
    <button
      title={label}
      onClick={onClick}
      disabled={disabled}
      onMouseEnter={() => setHov(true)}
      onMouseLeave={() => setHov(false)}
      style={{
        display: "inline-flex", alignItems: "center", justifyContent: "center",
        gap: 4,
        minWidth: wide ? "auto" : 30, height: 30,
        padding: wide ? "0 10px" : "0 6px",
        borderRadius: 6,
        border: active ? `1.5px solid ${T.pinkLight}` : "1.5px solid transparent",
        background: active
          ? T.primaryPale
          : hov ? "rgba(240,96,144,.1)" : "transparent",
        color: active ? T.primary : hov ? T.primary : T.textMid,
        fontSize: wide ? 12 : 14,
        fontFamily: F.ui,
        fontWeight: 600,
        cursor: disabled ? "default" : "pointer",
        opacity: disabled ? 0.4 : 1,
        transition: "all .15s ease",
        flexShrink: 0,
      }}
    >
      {icon}{wide && <span style={{ fontSize: 11 }}>{label}</span>}
    </button>
  );
}

function Divider() {
  return (
    <div style={{
      width: 1, height: 20, background: T.pinkLight,
      margin: "0 4px", flexShrink: 0,
    }} />
  );
}

// ─────────────────────────────────────────────
// COVER UPLOADER (compact)
// ─────────────────────────────────────────────
function CoverThumb({ cover, onChange, onRemove }) {
  const ref = useRef();
  const [hov, setHov] = useState(false);
  return (
    <div style={{ display: "flex", alignItems: "center", gap: 10 }}>
      <div
        onClick={() => ref.current.click()}
        onMouseEnter={() => setHov(true)}
        onMouseLeave={() => setHov(false)}
        style={{
          width: 52, height: 52, borderRadius: 8, flexShrink: 0,
          background: cover
            ? `url('${cover}') center/cover`
            : `linear-gradient(135deg,${T.pinkLight},#d0a8f0)`,
          border: `2px dashed ${hov ? T.primary : T.pinkLight}`,
          cursor: "pointer", position: "relative", overflow: "hidden",
          transition: "border-color .2s",
        }}
      >
        {(!cover || hov) && (
          <div style={{
            position: "absolute", inset: 0,
            background: cover ? "rgba(240,80,140,.45)" : "transparent",
            display: "flex", alignItems: "center", justifyContent: "center",
            fontSize: cover ? 18 : 20,
          }}>
            {cover ? "✎" : "📷"}
          </div>
        )}
        <input ref={ref} type="file" accept="image/*" style={{ display: "none" }}
          onChange={(e) => {
            const f = e.target.files[0]; if (!f) return;
            const r = new FileReader();
            r.onload = (ev) => onChange(ev.target.result);
            r.readAsDataURL(f);
          }} />
      </div>
      <div style={{ minWidth: 0 }}>
        <div style={{ fontFamily: F.ui, fontSize: 11, fontWeight: 600, color: T.textSoft, marginBottom: 4 }}>
          Cover Photo
        </div>
        <div style={{ display: "flex", gap: 6 }}>
          <button onClick={() => ref.current.click()} style={sideBtn}>{cover ? "Change" : "Upload"}</button>
          {cover && <button onClick={onRemove} style={{ ...sideBtn, color: "#e04060" }}>Remove</button>}
        </div>
      </div>
    </div>
  );
}
const sideBtn = {
  background: "white", border: `1px solid ${T.pinkLight}`,
  borderRadius: 6, padding: "3px 10px",
  fontFamily: "'DM Sans',sans-serif", fontSize: 11, fontWeight: 600,
  color: T.textMid, cursor: "pointer",
};

// ─────────────────────────────────────────────
// STORY CARD (sidebar list item)
// ─────────────────────────────────────────────
function StoryItem({ story, active, onSelect, onDelete }) {
  const [hov, setHov] = useState(false);
  const [menuOpen, setMenuOpen] = useState(false);
  const wc = wordCount(story.content);

  return (
    <div
      onClick={() => onSelect(story)}
      onMouseEnter={() => setHov(true)}
      onMouseLeave={() => { setHov(false); setMenuOpen(false); }}
      style={{
        display: "flex", alignItems: "center", gap: 10,
        padding: "10px 14px",
        borderRadius: 10,
        background: active
          ? `linear-gradient(135deg,${T.primaryPale},rgba(200,128,232,.12))`
          : hov ? "rgba(240,96,144,.07)" : "transparent",
        border: active ? `1.5px solid ${T.pinkLight}` : "1.5px solid transparent",
        cursor: "pointer", transition: "all .15s ease",
        position: "relative",
      }}
    >
      {/* mini cover */}
      <div style={{
        width: 38, height: 50, borderRadius: 5, flexShrink: 0,
        background: story.cover
          ? `url('${story.cover}') center/cover`
          : `linear-gradient(160deg,${T.pinkLight},#d8a8f0)`,
        boxShadow: "0 1px 4px rgba(220,100,160,.2)",
        position: "relative", overflow: "hidden",
      }}>
        {/* spine line */}
        <div style={{ position: "absolute", left: 6, top: 0, bottom: 0, width: 2, background: "rgba(255,255,255,.35)" }} />
      </div>

      <div style={{ flex: 1, minWidth: 0 }}>
        <div style={{
          fontFamily: F.display, fontSize: 13, fontWeight: 700,
          color: active ? T.primary : T.textDark,
          whiteSpace: "nowrap", overflow: "hidden", textOverflow: "ellipsis",
          marginBottom: 2,
        }}>
          {story.title || "Untitled Story"}
        </div>
        <div style={{ fontFamily: F.ui, fontSize: 10.5, color: T.textFaint }}>
          {wc} words · {fmtDate(story.updatedAt || story.createdAt)}
        </div>
      </div>

      {/* kebab */}
      {(hov || menuOpen) && (
        <button
          onClick={(e) => { e.stopPropagation(); setMenuOpen((o) => !o); }}
          style={{
            background: "none", border: "none", cursor: "pointer",
            color: T.textSoft, fontSize: 16, padding: "0 2px",
            lineHeight: 1, borderRadius: 4,
          }}
        >⋯</button>
      )}
      {menuOpen && (
        <div style={{
          position: "absolute", right: 10, top: "100%", zIndex: 50,
          background: "white", border: `1px solid ${T.pinkLight}`,
          borderRadius: 8, boxShadow: "0 4px 20px rgba(220,100,160,.18)",
          overflow: "hidden", minWidth: 130,
        }}>
          <button
            onClick={(e) => { e.stopPropagation(); setMenuOpen(false); onDelete(story.id); }}
            style={{
              display: "block", width: "100%", textAlign: "left",
              padding: "9px 14px", background: "none", border: "none",
              fontFamily: F.ui, fontSize: 12, fontWeight: 600,
              color: "#d02050", cursor: "pointer",
            }}
            onMouseEnter={(e) => (e.currentTarget.style.background = "#fff0f4")}
            onMouseLeave={(e) => (e.currentTarget.style.background = "none")}
          >
            🗑 Delete story
          </button>
        </div>
      )}
    </div>
  );
}

// ─────────────────────────────────────────────
// FORMATTING TOOLBAR
// ─────────────────────────────────────────────
const FONT_SIZES = ["12", "14", "16", "18", "20", "24", "28", "32", "36"];
const FONT_FAMILIES = ["Playfair Display", "Georgia", "Times New Roman", "Courier New", "Arial"];

function Toolbar({ onFormat, fontSize, setFontSize, fontFamily, setFontFamily }) {
  const fmt = (cmd, val) => { document.execCommand(cmd, false, val); };

  return (
    <div style={{
      display: "flex", alignItems: "center", flexWrap: "wrap",
      gap: 2, padding: "6px 16px",
      background: T.toolbarBg,
      borderBottom: `1px solid ${T.toolbarBorder}`,
      minHeight: 44,
    }}>
      {/* Font family */}
      <select
        value={fontFamily}
        onChange={(e) => { setFontFamily(e.target.value); fmt("fontName", e.target.value); }}
        style={selectStyle}
      >
        {FONT_FAMILIES.map((f) => <option key={f}>{f}</option>)}
      </select>

      {/* Font size */}
      <select
        value={fontSize}
        onChange={(e) => { setFontSize(e.target.value); fmt("fontSize", "3"); /* proxy */ }}
        style={{ ...selectStyle, width: 52 }}
      >
        {FONT_SIZES.map((s) => <option key={s}>{s}</option>)}
      </select>

      <Divider />

      <IconBtn label="Bold"      icon={<b>B</b>}  onClick={() => fmt("bold")} />
      <IconBtn label="Italic"    icon={<i>I</i>}  onClick={() => fmt("italic")} />
      <IconBtn label="Underline" icon={<u>U</u>}  onClick={() => fmt("underline")} />

      <Divider />

      <IconBtn label="Align Left"   icon="⬤≡" onClick={() => fmt("justifyLeft")} />
      <IconBtn label="Align Center" icon="≡"  onClick={() => fmt("justifyCenter")} />
      <IconBtn label="Align Right"  icon="≡⬤" onClick={() => fmt("justifyRight")} />

      <Divider />

      <IconBtn label="Bullet List"   icon="• ≡" onClick={() => fmt("insertUnorderedList")} />
      <IconBtn label="Numbered List" icon="1 ≡" onClick={() => fmt("insertOrderedList")} />

      <Divider />

      <IconBtn label="Undo" icon="↩" onClick={() => fmt("undo")} />
      <IconBtn label="Redo" icon="↪" onClick={() => fmt("redo")} />

      <Divider />

      {/* Heading styles */}
      <select
        onChange={(e) => { fmt("formatBlock", e.target.value); e.target.value = "p"; }}
        defaultValue="p"
        style={selectStyle}
      >
        <option value="p">Normal</option>
        <option value="h1">Heading 1</option>
        <option value="h2">Heading 2</option>
        <option value="h3">Heading 3</option>
        <option value="blockquote">Quote</option>
      </select>
    </div>
  );
}

const selectStyle = {
  background: "white",
  border: `1px solid ${T.pinkLight}`,
  borderRadius: 6,
  padding: "4px 6px",
  fontFamily: "'DM Sans',sans-serif",
  fontSize: 12,
  color: T.textDark,
  outline: "none",
  cursor: "pointer",
  height: 28,
  width: 140,
};

// ─────────────────────────────────────────────
// EDITOR PANEL (Google-Docs-style)
// ─────────────────────────────────────────────
function EditorPanel({ story, onChange }) {
  const editorRef = useRef(null);
  const [fontSize, setFontSize] = useState("16");
  const [fontFamily, setFontFamily] = useState("Playfair Display");
  const [wordCt, setWordCt] = useState(wordCount(story.content));

  // Init content
  useEffect(() => {
    if (editorRef.current) {
      editorRef.current.innerHTML = story.content || "";
      setWordCt(wordCount(editorRef.current.innerText));
    }
  }, [story.id]);

  const handleInput = useCallback(() => {
    if (!editorRef.current) return;
    const text = editorRef.current.innerHTML;
    const plain = editorRef.current.innerText;
    setWordCt(wordCount(plain));
    onChange({ content: text });
  }, [onChange]);

  return (
    <div style={{ display: "flex", flexDirection: "column", flex: 1, overflow: "hidden" }}>
      <Toolbar fontSize={fontSize} setFontSize={setFontSize} fontFamily={fontFamily} setFontFamily={setFontFamily} />

      {/* Paper scroll area */}
      <div style={{
        flex: 1, overflowY: "auto",
        background: T.appBg,
        padding: "32px 0 60px",
        display: "flex", flexDirection: "column", alignItems: "center",
      }}>
        {/* Page shadow/title banner */}
        <div style={{
          width: "min(780px, 95%)",
          background: story.cover
            ? `url('${story.cover}') center/cover`
            : `linear-gradient(135deg,${T.pinkLight} 0%,#d8b0f8 100%)`,
          height: 160, borderRadius: "12px 12px 0 0",
          position: "relative", overflow: "hidden",
          boxShadow: "0 -2px 12px rgba(220,100,160,.12)",
        }}>
          <div style={{
            position: "absolute", inset: 0,
            background: "linear-gradient(to bottom, rgba(240,80,140,.15) 0%, rgba(200,40,110,.55) 100%)",
          }} />
          <div style={{
            position: "absolute", bottom: 20, left: 32, right: 32,
            fontFamily: F.display, fontSize: 28, fontWeight: 700,
            color: "white", textShadow: "0 2px 12px rgba(160,20,80,.5)",
            lineHeight: 1.2,
          }}>
            {story.title || <span style={{ opacity: .5 }}>Untitled Story</span>}
          </div>
        </div>

        {/* White paper page */}
        <div style={{
          width: "min(780px, 95%)",
          background: T.pageBg,
          boxShadow: T.pageShad,
          borderRadius: "0 0 4px 4px",
          minHeight: 900,
          padding: "48px 72px 72px",
        }}>
          {/* Title input */}
          <input
            value={story.title}
            onChange={(e) => onChange({ title: e.target.value })}
            placeholder="Story title…"
            style={{
              width: "100%",
              fontFamily: F.display,
              fontSize: 32,
              fontWeight: 700,
              color: T.textDark,
              background: "none",
              border: "none",
              outline: "none",
              borderBottom: `2px solid ${T.pinkFaint}`,
              paddingBottom: 12,
              marginBottom: 28,
              letterSpacing: "-.01em",
            }}
            onFocus={(e) => (e.target.style.borderColor = T.pinkMid)}
            onBlur={(e) => (e.target.style.borderColor = T.pinkFaint)}
          />

          {/* Author line */}
          <div style={{ display: "flex", alignItems: "center", gap: 8, marginBottom: 32 }}>
            <div style={{
              width: 28, height: 28, borderRadius: "50%",
              background: `linear-gradient(135deg,${T.primary},${T.lilac})`,
              display: "flex", alignItems: "center", justifyContent: "center",
              fontFamily: F.ui, fontSize: 12, color: "white", fontWeight: 700, flexShrink: 0,
            }}>
              {(story.author || "A")[0].toUpperCase()}
            </div>
            <input
              value={story.author}
              onChange={(e) => onChange({ author: e.target.value })}
              placeholder="Author name…"
              style={{
                fontFamily: F.ui, fontSize: 13, fontWeight: 600,
                color: T.textMid, background: "none", border: "none",
                outline: "none", borderBottom: `1px solid ${T.pinkFaint}`,
              }}
              onFocus={(e) => (e.target.style.borderColor = T.pinkMid)}
              onBlur={(e) => (e.target.style.borderColor = T.pinkFaint)}
            />
            <span style={{ fontFamily: F.ui, fontSize: 12, color: T.textFaint }}>·</span>
            <span style={{ fontFamily: F.ui, fontSize: 12, color: T.textFaint }}>
              {fmtDate(story.updatedAt || story.createdAt)}
            </span>
            <span style={{ fontFamily: F.ui, fontSize: 12, color: T.textFaint }}>·</span>
            <span style={{ fontFamily: F.ui, fontSize: 12, color: T.textFaint }}>
              {wordCt} words
            </span>
          </div>

          {/* Rich-text body */}
          <div
            ref={editorRef}
            contentEditable
            suppressContentEditableWarning
            onInput={handleInput}
            data-placeholder="Start writing your story… ✦"
            style={{
              fontFamily: fontFamily + ", Georgia, serif",
              fontSize: fontSize + "px",
              lineHeight: 1.85,
              color: T.textDark,
              outline: "none",
              minHeight: 600,
              caretColor: T.primary,
            }}
          />
        </div>
      </div>
    </div>
  );
}

// ─────────────────────────────────────────────
// TOP MENU BAR
// ─────────────────────────────────────────────
function TopBar({ story, onSave, saving, onExport, exporting, onNewStory }) {
  return (
    <div style={{
      display: "flex", alignItems: "center",
      padding: "0 16px",
      height: 52,
      background: T.topbarBg,
      borderBottom: `1px solid ${T.topbarBorder}`,
      gap: 12,
      flexShrink: 0,
      zIndex: 10,
    }}>
      {/* Logo */}
      <div style={{
        fontFamily: "'Playfair Display', serif",
        fontSize: 19,
        fontWeight: 700,
        background: `linear-gradient(135deg,${T.primary},${T.lilac})`,
        WebkitBackgroundClip: "text", WebkitTextFillColor: "transparent",
        backgroundClip: "text",
        whiteSpace: "nowrap",
        letterSpacing: "-.01em",
        marginRight: 4,
      }}>
        ✦ StoryForge
      </div>

      <div style={{ flex: 1 }} />

      {/* Saving indicator */}
      {saving && (
        <span style={{ fontFamily: F.ui, fontSize: 12, color: T.textFaint }}>
          Saving…
        </span>
      )}

      {/* Actions */}
      <button
        onClick={onExport}
        disabled={exporting}
        style={{
          background: "white",
          border: `1.5px solid ${T.pinkLight}`,
          borderRadius: 8,
          padding: "6px 16px",
          fontFamily: F.ui, fontSize: 13, fontWeight: 600,
          color: T.textMid, cursor: exporting ? "default" : "pointer",
          opacity: exporting ? 0.7 : 1,
          transition: "all .15s",
        }}
        onMouseEnter={(e) => { if (!exporting) { e.currentTarget.style.background = T.pinkFaint; e.currentTarget.style.color = T.primary; }}}
        onMouseLeave={(e) => { e.currentTarget.style.background = "white"; e.currentTarget.style.color = T.textMid; }}
      >
        {exporting ? "Exporting…" : "⬇ Export PDF"}
      </button>

      <button
        onClick={onSave}
        style={{
          background: `linear-gradient(135deg,${T.primary},${T.pinkMid})`,
          border: "none", borderRadius: 8,
          padding: "7px 20px",
          fontFamily: F.ui, fontSize: 13, fontWeight: 700,
          color: "white", cursor: "pointer",
          boxShadow: "0 2px 10px rgba(232,51,122,.3)",
          transition: "all .15s",
        }}
        onMouseEnter={(e) => (e.currentTarget.style.boxShadow = "0 4px 18px rgba(232,51,122,.45)")}
        onMouseLeave={(e) => (e.currentTarget.style.boxShadow = "0 2px 10px rgba(232,51,122,.3)")}
      >
        {saving ? "✓ Saved" : "Save"}
      </button>
    </div>
  );
}

// ─────────────────────────────────────────────
// SIDEBAR
// ─────────────────────────────────────────────
function Sidebar({ stories, activeId, onSelect, onNew, onDelete }) {
  const [search, setSearch] = useState("");
  const filtered = stories.filter((s) =>
    (s.title + (s.content || "")).toLowerCase().includes(search.toLowerCase())
  );

  return (
    <div style={{
      width: 260, flexShrink: 0,
      background: T.sidebarBg,
      borderRight: `1px solid ${T.sidebarBorder}`,
      display: "flex", flexDirection: "column",
      overflow: "hidden",
    }}>
      {/* Sidebar header */}
      <div style={{
        padding: "14px 14px 10px",
        borderBottom: `1px solid ${T.sidebarBorder}`,
        flexShrink: 0,
      }}>
        <button
          onClick={onNew}
          style={{
            display: "flex", alignItems: "center", justifyContent: "center", gap: 7,
            width: "100%", padding: "9px 0",
            background: `linear-gradient(135deg,${T.primary},${T.pinkMid})`,
            border: "none", borderRadius: 10,
            fontFamily: F.ui, fontSize: 13, fontWeight: 700,
            color: "white", cursor: "pointer",
            boxShadow: "0 2px 10px rgba(232,51,122,.28)",
            transition: "box-shadow .15s",
          }}
          onMouseEnter={(e) => (e.currentTarget.style.boxShadow = "0 4px 18px rgba(232,51,122,.42)")}
          onMouseLeave={(e) => (e.currentTarget.style.boxShadow = "0 2px 10px rgba(232,51,122,.28)")}
        >
          <span style={{ fontSize: 16 }}>✦</span> New Story
        </button>

        {/* Search */}
        <div style={{ position: "relative", marginTop: 10 }}>
          <span style={{
            position: "absolute", left: 10, top: "50%", transform: "translateY(-50%)",
            fontSize: 13, color: T.textFaint, pointerEvents: "none",
          }}>🔍</span>
          <input
            value={search}
            onChange={(e) => setSearch(e.target.value)}
            placeholder="Search stories…"
            style={{
              width: "100%", padding: "7px 10px 7px 30px",
              background: "white", border: `1px solid ${T.pinkLight}`,
              borderRadius: 8, fontFamily: F.ui, fontSize: 12,
              color: T.textDark, outline: "none", boxSizing: "border-box",
            }}
            onFocus={(e) => (e.target.style.borderColor = T.primary)}
            onBlur={(e) => (e.target.style.borderColor = T.pinkLight)}
          />
        </div>
      </div>

      {/* Section label */}
      <div style={{
        padding: "10px 14px 6px",
        fontFamily: F.ui, fontSize: 10.5, fontWeight: 700,
        color: T.textFaint, letterSpacing: "0.08em", textTransform: "uppercase",
        flexShrink: 0,
      }}>
        My Stories ({filtered.length})
      </div>

      {/* List */}
      <div style={{ flex: 1, overflowY: "auto", padding: "4px 8px 20px" }}>
        {filtered.length === 0 ? (
          <div style={{
            textAlign: "center", padding: "36px 16px",
            fontFamily: F.ui, fontSize: 12, color: T.textFaint, fontStyle: "italic",
          }}>
            {stories.length === 0 ? "No stories yet.\nClick + New Story to begin ✦" : "No results found"}
          </div>
        ) : (
          filtered.map((s) => (
            <StoryItem
              key={s.id}
              story={s}
              active={s.id === activeId}
              onSelect={onSelect}
              onDelete={onDelete}
            />
          ))
        )}
      </div>

      {/* Footer */}
      <div style={{
        padding: "12px 14px",
        borderTop: `1px solid ${T.sidebarBorder}`,
        fontFamily: F.ui, fontSize: 10.5, color: T.textFaint,
        textAlign: "center", flexShrink: 0,
      }}>
        ♡ StoryForge · Write your world
      </div>
    </div>
  );
}

// ─────────────────────────────────────────────
// RIGHT PANEL — story details / cover / stats
// ─────────────────────────────────────────────
function RightPanel({ story, onChange }) {
  if (!story) return null;
  const wc = wordCount(story.content?.replace(/<[^>]+>/g, " "));
  const readMin = Math.max(1, Math.ceil(wc / 250));

  return (
    <div style={{
      width: 220, flexShrink: 0,
      background: T.sidebarBg,
      borderLeft: `1px solid ${T.sidebarBorder}`,
      display: "flex", flexDirection: "column",
      padding: "20px 14px",
      gap: 20, overflowY: "auto",
    }}>
      <div style={{ fontFamily: F.ui, fontSize: 11, fontWeight: 700, color: T.textFaint, textTransform: "uppercase", letterSpacing: "0.08em" }}>
        Story Details
      </div>

      {/* Cover */}
      <CoverThumb
        cover={story.cover}
        onChange={(cover) => onChange({ cover })}
        onRemove={() => onChange({ cover: null })}
      />

      {/* Genre tag */}
      <div>
        <label style={labelStyle}>Genre / Tags</label>
        <input
          value={story.genre || ""}
          onChange={(e) => onChange({ genre: e.target.value })}
          placeholder="Romance, Fantasy…"
          style={fieldStyle}
          onFocus={(e) => (e.target.style.borderColor = T.primary)}
          onBlur={(e) => (e.target.style.borderColor = T.pinkLight)}
        />
      </div>

      {/* Description */}
      <div>
        <label style={labelStyle}>Description</label>
        <textarea
          value={story.desc || ""}
          onChange={(e) => onChange({ desc: e.target.value })}
          placeholder="A short blurb…"
          rows={4}
          style={{ ...fieldStyle, resize: "none", lineHeight: 1.6 }}
          onFocus={(e) => (e.target.style.borderColor = T.primary)}
          onBlur={(e) => (e.target.style.borderColor = T.pinkLight)}
        />
      </div>

      {/* Stats card */}
      <div style={{
        background: `linear-gradient(135deg,${T.primaryPale},rgba(200,128,232,.12))`,
        border: `1.5px solid ${T.pinkLight}`,
        borderRadius: 12, padding: "14px 12px",
      }}>
        <div style={{ fontFamily: F.ui, fontSize: 10.5, fontWeight: 700, color: T.textSoft, textTransform: "uppercase", letterSpacing: "0.07em", marginBottom: 10 }}>
          ✦ Statistics
        </div>
        {[
          ["Words", wc.toLocaleString()],
          ["Characters", (story.content?.replace(/<[^>]+>/g, "")?.length || 0).toLocaleString()],
          ["Read time", `${readMin} min`],
          ["Created", fmtDate(story.createdAt)],
          ["Updated", fmtDate(story.updatedAt || story.createdAt)],
        ].map(([k, v]) => (
          <div key={k} style={{ display: "flex", justifyContent: "space-between", marginBottom: 7 }}>
            <span style={{ fontFamily: F.ui, fontSize: 11.5, color: T.textSoft }}>{k}</span>
            <span style={{ fontFamily: F.ui, fontSize: 11.5, color: T.textDark, fontWeight: 600 }}>{v}</span>
          </div>
        ))}
      </div>

      {/* Status */}
      <div>
        <label style={labelStyle}>Status</label>
        <select
          value={story.status || "drafting"}
          onChange={(e) => onChange({ status: e.target.value })}
          style={{ ...fieldStyle, cursor: "pointer" }}
        >
          <option value="drafting">✏️ Drafting</option>
          <option value="editing">🔍 Editing</option>
          <option value="complete">✅ Complete</option>
          <option value="published">🌸 Published</option>
        </select>
      </div>
    </div>
  );
}

const labelStyle = {
  display: "block", fontFamily: "'DM Sans',sans-serif",
  fontSize: 10.5, fontWeight: 700, color: T.textSoft,
  textTransform: "uppercase", letterSpacing: "0.07em", marginBottom: 5,
};
const fieldStyle = {
  width: "100%", background: "white",
  border: `1px solid ${T.pinkLight}`,
  borderRadius: 8, padding: "8px 10px",
  fontFamily: "'DM Sans',sans-serif", fontSize: 12.5,
  color: T.textDark, outline: "none", boxSizing: "border-box",
  transition: "border-color .15s",
};

// ─────────────────────────────────────────────
// WELCOME / EMPTY STATE
// ─────────────────────────────────────────────
function Welcome({ onNew }) {
  return (
    <div style={{
      flex: 1, display: "flex", flexDirection: "column",
      alignItems: "center", justifyContent: "center",
      background: T.appBg, gap: 20, textAlign: "center", padding: 40,
    }}>
      <div style={{
        width: 120, height: 120, borderRadius: "50%",
        background: `linear-gradient(135deg,${T.pinkLight},#d8b0f8)`,
        display: "flex", alignItems: "center", justifyContent: "center",
        fontSize: 52, boxShadow: "0 8px 32px rgba(220,100,160,.2)",
      }}>
        📖
      </div>
      <div>
        <div style={{ fontFamily: F.display, fontSize: 28, fontWeight: 700, color: T.textDark, marginBottom: 8 }}>
          Your stories live here
        </div>
        <p style={{ fontFamily: F.ui, fontSize: 14, color: T.textSoft, lineHeight: 1.7, maxWidth: 340 }}>
          Select a story from the sidebar to start editing, or create a new one. Add a cover photo and download as a beautiful PDF.
        </p>
      </div>
      <button
        onClick={onNew}
        style={{
          background: `linear-gradient(135deg,${T.primary},${T.pinkMid})`,
          border: "none", borderRadius: 12,
          padding: "12px 32px",
          fontFamily: F.ui, fontSize: 14, fontWeight: 700,
          color: "white", cursor: "pointer",
          boxShadow: "0 4px 20px rgba(232,51,122,.3)",
          transition: "all .2s",
        }}
        onMouseEnter={(e) => (e.currentTarget.style.boxShadow = "0 6px 28px rgba(232,51,122,.45)")}
        onMouseLeave={(e) => (e.currentTarget.style.boxShadow = "0 4px 20px rgba(232,51,122,.3)")}
      >
        ✦ Create your first story
      </button>
    </div>
  );
}

// ─────────────────────────────────────────────
// ROOT APP
// ─────────────────────────────────────────────
export default function StoryForge() {
  const [stories, setStories] = useState([]);
  const [activeId, setActiveId] = useState(null);
  const [saving, setSaving] = useState(false);
  const [exporting, setExporting] = useState(false);
  const saveTimer = useRef(null);

  const active = stories.find((s) => s.id === activeId) || null;

  const createNew = () => {
    const s = {
      id: genId(), title: "", author: "", content: "",
      cover: null, genre: "", desc: "", status: "drafting",
      createdAt: Date.now(), updatedAt: Date.now(),
    };
    setStories((prev) => [s, ...prev]);
    setActiveId(s.id);
  };

  const handleChange = useCallback((patch) => {
    setStories((prev) =>
      prev.map((s) => s.id === activeId ? { ...s, ...patch, updatedAt: Date.now() } : s)
    );
    // auto-save indicator
    clearTimeout(saveTimer.current);
    setSaving(true);
    saveTimer.current = setTimeout(() => setSaving(false), 1200);
  }, [activeId]);

  const handleSave = () => {
    setSaving(true);
    setTimeout(() => setSaving(false), 900);
  };

  const handleDelete = (id) => {
    if (!window.confirm("Delete this story?")) return;
    setStories((prev) => prev.filter((s) => s.id !== id));
    if (activeId === id) setActiveId(null);
  };

  const handleExport = async () => {
    if (!active) return;
    setExporting(true);
    exportPDF({
      ...active,
      content: active.content?.replace(/<[^>]+>/g, (m) => {
        if (m === "<br>" || m === "<br/>" || m === "<br />") return "\n";
        if (m.startsWith("</p") || m.startsWith("</div") || m.startsWith("</h")) return "\n\n";
        return " ";
      }) || "",
    });
    setTimeout(() => setExporting(false), 1800);
  };

  return (
    <div style={{
      display: "flex", flexDirection: "column",
      height: "100vh", overflow: "hidden",
      fontFamily: F.ui, background: T.appBg,
    }}>
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=DM+Sans:wght@400;500;600;700&display=swap');
        * { box-sizing: border-box; }
        [contenteditable]:empty:before {
          content: attr(data-placeholder);
          color: rgba(180,120,160,.4);
          pointer-events: none;
          font-style: italic;
        }
        [contenteditable] h1 { font-size: 2em; margin: .6em 0 .3em; color: #c01860; }
        [contenteditable] h2 { font-size: 1.5em; margin: .6em 0 .3em; color: #a01050; }
        [contenteditable] h3 { font-size: 1.2em; margin: .5em 0 .25em; color: #901040; }
        [contenteditable] blockquote {
          border-left: 3px solid #f0c0d8; margin: 1em 0;
          padding: .5em 1.2em; color: #9a5070; font-style: italic;
          background: #fff5fa; border-radius: 0 8px 8px 0;
        }
        [contenteditable] ul, [contenteditable] ol { padding-left: 1.6em; margin: .6em 0; }
        [contenteditable] li { margin-bottom: .3em; }
        ::-webkit-scrollbar { width: 6px; height: 6px; }
        ::-webkit-scrollbar-track { background: transparent; }
        ::-webkit-scrollbar-thumb { background: rgba(232,80,150,.2); border-radius: 6px; }
        ::-webkit-scrollbar-thumb:hover { background: rgba(232,80,150,.4); }
        input::placeholder, textarea::placeholder { color: rgba(190,140,170,.5); }
        select option { font-family: 'DM Sans', sans-serif; }
      `}</style>

      {/* Top bar */}
      <TopBar
        story={active}
        onSave={handleSave}
        saving={saving}
        onExport={handleExport}
        exporting={exporting}
        onNewStory={createNew}
      />

      {/* Body: sidebar + editor + right panel */}
      <div style={{ flex: 1, display: "flex", overflow: "hidden" }}>
        <Sidebar
          stories={stories}
          activeId={activeId}
          onSelect={(s) => setActiveId(s.id)}
          onNew={createNew}
          onDelete={handleDelete}
        />

        {active ? (
          <>
            <EditorPanel
              key={active.id}
              story={active}
              onChange={handleChange}
            />
            <RightPanel story={active} onChange={handleChange} />
          </>
        ) : (
          <Welcome onNew={createNew} />
        )}
      </div>
    </div>
  );
}
