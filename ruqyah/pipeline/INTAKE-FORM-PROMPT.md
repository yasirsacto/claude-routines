# Ruqyah Intake Form — build prompt for Cowork

Paste everything between the lines into Cowork. Replace **[LANGUAGE]** with the client's
language (assumed **Dari**) before pasting. When the answers come back, give them to Claude
in the pipeline session and a treatment plan is generated the same way as the English form.

---

Build me a bilingual intake form called **"Ruqyah Intake / فورم معلومات رقیه"** for a Ruqyah
(Islamic spiritual healing) treatment service. Requirements:

**Format and audience**
- A Google Form (preferred; link it to a response Sheet) — if that's not possible, a clean
  printable document with the same questions in the same order.
- Every question and every answer option must appear in BOTH English and **[LANGUAGE]**,
  English first, the [LANGUAGE] translation directly underneath in its own script. Use
  respectful, simple, spoken-register [LANGUAGE] — the respondent may have the form read
  aloud to them by a family member, so avoid literary or technical vocabulary. Keep Islamic
  terms in their familiar form ([LANGUAGE] speakers know salah/namaz, ta'weez, jadu, nazar,
  jinn — use those words, not academic translations).
- A short intro at the top (both languages): "These questions help us prepare your Ruqyah
  treatment plan. Answer honestly; there are no wrong answers. This is not medical advice —
  continue any treatment from your doctor. A family member may fill this form for you."
- Unless marked otherwise, questions are Yes/No choices. Keep my answer option wording
  EXACTLY as given (the treatment system maps on these exact phrases).

**Section A — About the person** (all required)
1. Name of person experiencing symptoms (short text)
2. Age (number)
3. Gender (Male / Female)
4. Marital status (Married / Not married / Widowed / Divorced)
5. How do we contact you? (Phone / Email / WhatsApp)
6. Phone number or email (short text)
7. Who is filling this form? (The person themselves / A family member on their behalf)

**Section B — Mental and emotional states**
8. Do you experience any of the following? (checkboxes, choose all that apply):
   Anger · Fear · Confusion · Lack of concentration · Lack of self confidence ·
   Indecisiveness · Forgetfulness · Anxiety · Sadness · Suicidal thoughts ·
   Blank out or lose track while having conversations · Overthinking

**Section C — Health** (each Yes/No unless noted)
9. Do you have any unusual illness which doctors cannot explain, say is rare, or give an
   unusual diagnosis?
10. Do you respond to medication?
11. Are you always sick, as if moving from one illness to another?
12. Do you get unusual pains, throbbing or pulsating feelings in the body?
13. (Women only) How are your monthly menstrual cycles? (Regular / Irregular / Painful and
    very uncomfortable / Excessive bleeding)
14. Are there any intimacy issues? (None / Lack of desire / Pain or difficulty / Prefer not
    to say)
15. Does your stomach bloat, then go down for a while, then bloat again, repeatedly?
16. Do you get heartburn, nausea or repeated vomiting with no medical explanation?
17. Are you currently under a doctor's care, or taking any medication? If yes, briefly for
    what. (short text — required)

**Section D — Blockages in life** (each Yes/No)
18. Do you have blockages in life — for example you cannot get a job?
19. Do you begin tasks or projects but they never reach completion?
20. Is it a challenge for you to get married or to maintain your marriage?
21. Are you always losing money, with no barakah in it, and cannot account for it?
22. Do you feel unusually distant or separated from close family?
23. Do you have a hard time communicating?
24. Do you feel you are always misunderstood, and this leads to arguments?
25. Is carrying out salah (namaz) and other religious duties a very big struggle?

**Section E — Sleep and dreams**
26. Do you experience any of the following in dreams or nightmares? (checkboxes):
    Snakes · Blood · Being chased or attacked · Falling · Water, rivers, floods ·
    Dead people, graves, funerals · High places or flying · Lions, dogs and other animals
    of prey · Urine or faeces · Fire or smoke · Children or babies · Sexual dreams ·
    Crowds of people, letters, numbers · Travel and vehicles · Bones or teeth · Dolls ·
    Raw meat · People doing rituals or magic · Rats, pigs, dead animals ·
    Other (please describe)
27. Do you feel you are falling while asleep, then realize you are still in bed? (Yes/No)
28. Are you pressed down while sleeping, as if someone holds you and you cannot speak or
    move? (Yes/No)
29. Do you wake up tired even after a full night's sleep? (Yes/No)

**Section F — Unusual experiences** (each Yes/No)
30. Do you get bruises, scratches or marks on your body you cannot account for?
31. Do you get poking pains, as if someone is stabbing or prodding you?
32. Do you feel something crawling on your body, or pins and needles, with no medical
    reason?
33. Do you hear unusual noises, buzzing, ringing, or voices talking to you or calling you?
34. Do you see movement from the corner of your eye, but nobody is there when you look?
35. When alone, do you feel someone is watching you?
36. Do you faint or get epileptic attacks / seizures?

**Section G — Background** (these guide the treatment)
37. When did these problems begin, and did anything happen in your life around that time
    (a death, an accident, a conflict, a marriage, a move)? (paragraph)
38. In ONE sentence, how would you describe your situation in your own words? (short text —
    e.g. "I keep going in circles", "I feel like I am carrying chains")
39. Have you ever worn or kept a ta'weez / amulet, or visited an aamil, healer or fortune
    teller about this? (Yes, currently / Yes, in the past / Never)
40. Does anyone else living in your home have similar problems? (Yes / No / Not sure)
41. Anything else you want us to know? (paragraph, optional)

Make questions 8, 17, 26, 37, 38 required along with Section A. Title the confirmation
message (both languages): "JazakAllah khair — your answers have been received. Your
treatment plan will be prepared and sent to you after review."

---

## Notes for Yasir (not part of the prompt)

- Sections A–F question wording matches the existing English "Ruqya Questionare" exactly
  where they overlap, so the same diagnosis mapping runs unchanged. Section G adds the four
  things the method's own intake interview asks that the old form missed: onset/trauma
  screen, the "key sentence" (its main symbolic-diagnosis tool), amulet history, and
  household spread.
- Q17 (doctor/medication) exists so the plan can carry accurate medical-care language; Q2/Q3
  drive the child and gender adaptations; Q7 records proxy filling for a client who does not
  read.
- When responses arrive: either share the new response Sheet with yasirsacto@gmail.com (the
  daily pipeline can watch a second sheet), or simply paste/forward one client's answers
  into the pipeline session — the plan comes back the same day. If the client answered in
  [LANGUAGE], send the answers as-is; translation is handled during processing, and the
  plan itself can be produced bilingually on request.
