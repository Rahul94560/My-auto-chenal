const GEMINI_KEY = "AQ.Ab8RN6LckdyMwrQdL3_xyNl7LxwDCINB_RvvxRkK7nSuopd6KQ";

function sham6bajeUpload() {
  var prompt = "Ek nayi funny husband wife comedy story likho, 100 shabdo me, Hindi me, halki double meaning comedy, no gali, end me punchline. Title bhi dena";

  var url = "https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent?key=" + GEMINI_KEY;

  var data = {
    contents: [{ parts: [{ text: prompt }] }]
  };

  var res = UrlFetchApp.fetch(url, { method: "post", contentType: "application/json", payload: JSON.stringify(data) });
  var text = JSON.parse(res.getContentText()).candidates[0].content.parts[0].text;

  Logger.log(text);

  // YAHI TEXT KAL SE YOUTUBE PE JAYEGA
  // Abhi ke liye ye log me dikhega, upload ke liye next step dekho
}

function timerLagao() {
  // Purana timer hatao
  var triggers = ScriptApp.getProjectTriggers();
  for (var i = 0; i < triggers.length; i++) {
    ScriptApp.deleteTrigger(triggers[i]);
  }
  // Naya timer - Roz Sham 6 baje
  ScriptApp.newTrigger("sham6bajeUpload").timeBased().atHour(18).everyDays(1).create();
}
