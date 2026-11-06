# digital-detection
Digital-detective
from IPython.display import HTML

case = { "title": "The Missing Laptop", "desc": "A high-end laptop disappeared from Lab 3 between 2:00-3:00 PM.", "suspects": ["Rahul", "Ananya", "Arjun", "Priya"], "correct": "Arjun", "explanation": "Keycard logs show Arjun's ID entered Lab 3 at 2:14 PM, and CCTV confirms his jacket in the doorway at that time.", "evidence": [ ("📹 CCTV", "2:15 PM - A hoodie-wearing figure enters Lab 3 with an empty backpack."), ("💬 Chat Logs", "Ananya to Priya (2:05 PM): 'Meeting you at canteen now.'"), ("👤 Witness", "Rahul: 'I was with Ananya in the canteen 2:00-2:45 PM.'"), ("🕐 Access Log", "Keycard #104 (Arjun) logged at Lab 3 door, 2:14 PM."), ], }

evidence_html = "".join(f'

{t}: {c}
' for t, c in case["evidence"]) options_html = "".join(f'{s}' for s in case["suspects"])
HTML(f"""

<style> body{{font-family:sans-serif}} .card{{background:#1e1e1e;color:#eee;padding:20px;border-radius:8px;max-width:600px}} .ev{{background:#2a2a2a;border-left:4px solid #00e676;padding:8px;margin:6px 0}} .btn{{background:#00e676;border:none;padding:8px 16px;border-radius:4px;cursor:pointer;font-weight:bold}} select{{padding:6px;margin:8px 0}} #result{{display:none;margin-top:12px;padding:10px;background:#252525;border-radius:6px}} </style>
🕵️ {case['title']}
{case['desc']}

📂 Evidence
{evidence_html}
🔍 Verdict
{options_html} Submit
<script> function checkAnswer() {{ const picked = document.getElementById('suspect').value; const correct = "{case['correct']}"; const solved = picked === correct; const r = document.getElementById('result'); r.style.display = 'block'; r.innerHTML = (solved ? "🎉 Case Solved! Score: 100/100" : "🔎 Not quite. Score: 35/100") + "

Actual Culprit: " + correct + "
{case['explanation']}"; }} </script> """)
