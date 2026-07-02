# Sample Conversations

## Example 1 — High confidence (silent correction)

**User:** can u chek if the fil was recieved corectly

**Without skill:**
> Did you mean "check if the file was received correctly"? Please confirm.

**With skill:**
> Checked the file — it was received correctly and no corruption was
> detected.

---

## Example 2 — Medium confidence (silent correction + short note)

**User:** the meeting is definately tommorow at 5

**Without skill:**
> Did you mean "definitely" and "tomorrow"?

**With skill:**
> Got it, I've noted the meeting for tomorrow at 5.
> (assuming: "definitely tomorrow")

---

## Example 3 — Low confidence (one clarifying question)

**User:** book a flite to Georgia

**With skill:**
> Just to confirm — did you mean Georgia the country, or Georgia, USA?

---

## Example 4 — Proper noun preserved (no false correction)

**User:** open the file called Recieved_Docs_Final.pdf

**With skill:**
> Opens the file exactly as named (`Recieved_Docs_Final.pdf`) — the
> filename itself is left untouched since it's a proper file name, even
> though "Recieved" looks like a typo.
