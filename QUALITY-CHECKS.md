# Quality checks — İlk Cümlem

Checked on 26 September 2026. These are checks of this delivered version, not a guarantee of identical behaviour on every device.

## English teacher-mode update

Added full English teaching guidance for all 17 lessons, including 51 speaking instructions, 17 practical missions, 34 usage-question explanations, the complete quiz key, the 30-day plan and eight assessment instructions. English settings, progress, vocabulary review and recording controls share the existing student record. The student view retains Turkish support.

The update was checked in a local JavaScript test harness with a lightweight DOM stub: all 102 teacher stage renders, all 102 original student quiz answers, switching to the matching student stage and back, shared progress, backup import validation, English error messages and saved view preference passed. These update checks do not establish a fresh visual/browser test; the earlier browser URL restriction was not bypassed. Desktop/mobile browser checks below describe the original student interface before the teacher-mode update.

## Course coverage

- 17 fully populated lessons; no locked or placeholder lessons.
- 189 lesson vocabulary entries representing 179 distinct words and chunks; the final lesson deliberately recycles earlier material.
- 114 bilingual model phrases and 111 dialogue lines across 17 dialogues.
- 51 speaking prompts and 17 practical speaking missions.
- 102 quiz questions, including 17 listening questions and 17 sentence-ordering exercises.
- A 30-day plan and the same eight speaking tasks for the initial and final self-assessments.
- English examples, Turkish explanations, translations, answer keys, and grammatical progression reviewed during authoring. This was not an independent review by a second teacher.

## Passed functional checks

Tested the delivered HTML as a local file in Edge's automated browser mode:

- Opened all six stages of all 17 lessons.
- Answered all 102 quiz questions correctly and verified their scores, including every sentence-ordering exercise.
- Confirmed that a wrong answer is not scored and receives corrective feedback.
- Checked vocabulary tracking, scheduled recall, hidden dialogue responses, speaking checkboxes, and the combined lesson-completion rule.
- Checked glossary search, a search containing HTML characters, daily-plan checkboxes, assessment scores, and notes.
- Reloaded the page and verified saved progress.
- Exported and imported a progress backup; rejected a malformed backup without changing progress; cancelled a reset without losing progress.
- Checked all main pages and the six lesson stages at a 390-pixel viewport. Fixed a settings-page overflow found during this check.
- Inspected desktop and mobile screenshots. No uncaught JavaScript errors occurred in the completed functional test.

## Audio checks and limits

- A virtual test microphone produced a nonempty, playable recording through the real MediaRecorder API; the recording could be downloaded.
- Leaving the recording page released the microphone.
- Microphone denial produced a Turkish explanation and returned to a usable state.
- Speech text, speed, language selection, and the missing-voice fallback were checked using a simulated synthesis voice.
- The automated browser listed three English voices, but **native speech playback returned a synthesis failure in this environment**. Attempts to create embedded narration through Windows speech were also blocked by local access restrictions. No embedded narration is included.
- Consequently, the lesson listening buttons rely on the learner's functioning browser/device English speech voice. Audible narration was not verified here. Test the voice in **Ses & ayarlar** on the actual learner's device before the first lesson.
- Recordings are for listening and comparison. Pronunciation is not automatically graded. Virtual microphone testing does not establish that the learner's physical microphone works.

## Delivery notes

The HTML contains the course and needs no account or external JavaScript libraries. Course text and exercises work offline. Browser voices may require internet. Progress is stored locally; recordings must be downloaded separately.

The app's in-app browser preview rejected the local-file URL. Open the delivered HTML in your own browser; this restriction does not remove any lesson content from the file.

## Current English-first revision

The current delivery replaces the language-mode interface with one English course and per-item Turkish reveal/hide buttons. Turkish support starts hidden and English remains visible when it is revealed. English vocabulary definitions and English quiz/review questions replace Turkish-first prompts.

Local JavaScript harness checks passed for all 179 vocabulary definitions, all 102 lesson-stage renders, hidden translation blocks, all 102 quiz answers, independent reveal/hide behaviour, unchanged progress during translation, all main routes, vocabulary/speaking tracking and backup compatibility. These are code/DOM-stub tests, not a fresh visual browser test. Earlier teacher-mode instructions above describe a superseded revision.
