<%*
let d = moment(tp.file.title, "YYYY-MM-DD");
let q = "Q" + (Math.floor(d.month() / 3) + 1);
let w = d.isoWeek().toString().padStart(2, '0');
-%>
---
week: '[[<% d.format("YYYY") %>-W<% w %>]]'
date: '<% tp.file.title %>'
cssclasses:
  - hide-properties
  - daily
  <% "- " + tp.date.now("dddd", 0, tp.file.title, "YYYYMMDD").toLowerCase() %>
---

## [[<% d.format("YYYY")%>]] / [[<%d.format("YYYY")%>-<% q %>|<% q %>]] / [[<% d.format("YYYY-MM") %>|<% d.format("MMMM") %>]] / [[<% d.format("YYYY") %>-W<% w %>|Week <% d.isoWeek() %>]]
# DAILY NOTE
##### ❮ [[<% d.clone().subtract(1, 'days').format("YYYY-MM-DD") %>]] | <% tp.file.title %> | [[<% d.clone().add(1, 'days').format("YYYY-MM-DD") %>]] ❯
---
### ☑️Tasks
<!-- DAILY_TASKS_START -->
<%*
const currentDate = moment(tp.file.title, "YYYY-MM-DD");
const startMarker = "<!-- DAILY_TASKS_START -->";
const endMarker = "<!-- DAILY_TASKS_END -->";
let pending = [];

const previousDaily = app.vault.getMarkdownFiles()
  .filter((file) => /^Calendar\/Daily\/\d{4}-\d{2}-\d{2}\.md$/.test(file.path))
  .map((file) => ({ file, date: moment(file.basename, "YYYY-MM-DD") }))
  .filter(({ date }) => date.isValid() && date.isBefore(currentDate, "day"))
  .sort((a, b) => b.date.valueOf() - a.date.valueOf())[0];

if (previousDaily) {
  const content = await app.vault.cachedRead(previousDaily.file);
  const start = content.indexOf(startMarker);
  const end = content.indexOf(endMarker);
  if (start !== -1 && end !== -1 && end > start) {
    const section = content.slice(start + startMarker.length, end);
    pending = section
      .split("\n")
      .map((line) => line.trimEnd())
      .filter((line) => /^\s*-\s\[\s\]\s+\S/.test(line));
  }
}

if (pending.length > 0) {
  tR += pending.join("\n");
} else {
  tR += "- [ ] ";
}
%>
<!-- DAILY_TASKS_END -->

---
### 📕Diary
#### Log

#### Success


---
### ⚛️Habits
#### Habits

---

### 🧾Today Activity
![[Today Activity.base]]
