# 📜 The Doomsday Algorithm

_A neat way to know the weekday of any date, past or future — even thousands of years away._

---

## 1️⃣ What is “Doomsday”?

> For every year there is one special weekday, called the **Doomsday**.
> All the following “easy dates” in that year fall on that same weekday:

| Month | Doomsday Dates (Normal Year) | Leap-Year Note   |
| ----- | ---------------------------- | ---------------- |
| Jan   | 3                            | 4 in leap years  |
| Feb   | 28                           | 29 in leap years |
| Mar   | 0 ( = Feb 28/29 ), 14        | —                |
| Apr   | 4                            | —                |
| May   | 9                            | —                |
| Jun   | 6                            | —                |
| Jul   | 11                           | —                |
| Aug   | 8                            | —                |
| Sep   | 5                            | —                |
| Oct   | 10                           | —                |
| Nov   | 7                            | —                |
| Dec   | 12                           | —                |

Once we know the **weekday of the Doomsday** for that year, any of those dates — and anything close to them — is easy to compute.

---

## 2️⃣ Find the **Doomsday of a Year**

Write the year as `CCYY` (century `CC`, year within century `YY`).

### Steps

| Step  | What to do                                    | Example for 2023   |
| ----- | --------------------------------------------- | ------------------ |
| **A** | Take the last two digits: `Y = YY`            | 23                 |
| **B** | Divide by 12 → `a = Y // 12`                  | 23 // 12 = 1       |
| **C** | Remainder after ÷12 → `b = Y % 12`            | 23 % 12 = 11       |
| **D** | Divide remainder by 4 → `c = b // 4`          | 11 // 4 = 2        |
| **E** | Sum: `s = a + b + c`                          | 1 + 11 + 2 = 14    |
| **F** | Add the **century anchor** (see next section) | anchor(2000s) = 2  |
| **G** | Take `mod 7` → gives the weekday number       | (14 + 2) mod 7 = 2 |

Weekday numbers (standard mapping):
`0 = Sun, 1 = Mon, 2 = Tue, 3 = Wed, 4 = Thu, 5 = Fri, 6 = Sat`.

So, **Doomsday(2023) = 2 = Tuesday**.

---

## 3️⃣ Century Anchor Values

For Gregorian dates the anchor depends only on the century:

| Centuries | Anchor (weekday number) | Weekday   |
| --------- | ----------------------: | --------- |
| 1600–1699 |                       2 | Tuesday   |
| 1700–1799 |                       0 | Sunday    |
| 1800–1899 |                       5 | Friday    |
| 1900–1999 |                       3 | Wednesday |
| 2000–2099 |                       2 | Tuesday   |
| 2100–2199 |                       0 | Sunday    |
| 2200–2299 |                       5 | Friday    |
| 2300–2399 |                       3 | Wednesday |

> Pattern repeats every **400 years**.

Formula if we prefer math:

$$
\text{Anchor} = \big(5 \times (C \bmod 4) + 2\big) \bmod 7
$$

(where $C$ is the century number, e.g. 20 for 2000–2099).

---

## 4️⃣ Use the Doomsday to find required date

1. Locate the nearest **doomsday date** in the same month.
2. Count days forward/backward (mod 7).
3. Add/subtract from the year’s doomsday weekday.

**Example:** 24 Dec 2023

- Doomsday(2023) = Tuesday.
- December’s anchor = 12 Dec = Tuesday.
- 24 – 12 = 12 days → 12 ≡ 5 (mod 7).
- Tuesday + 5 = **Sunday**.

---

## 5️⃣ Very far years (e.g. 4000+, 7000+)

The Gregorian cycle repeats every **400 years**.
So:

- To find Doomsday for 4000, reduce `4000 mod 400 = 0`. → same as year 0 in the cycle = **Tuesday**.
- For 7000: `7000 mod 400 = 200`; century = 70; apply the same steps with anchor = (5×(70%4)+2)%7.

> No matter how large the year, just bring it back by blocks of 400 and then use the same algorithm.

---

**Addition Logic:**

Once we’ve worked out the **Doomsday for the start of a century (or any base year)**, we can get the doomsday for the next few years just by **adding 1 each year and adding an extra 1 after a leap year** — always working mod 7.

For example, starting at the year 2000:

| Year | Rule                         | Doomsday |
| ---- | ---------------------------- | -------- |
| 2000 | base (Tuesday = 2)           | 2        |
| 2001 | +1                           | 3 (Wed)  |
| 2002 | +1                           | 4 (Thu)  |
| 2003 | +1                           | 5 (Fri)  |
| 2004 | +1 then +1 again (leap year) | 0 (Sun)  |
| 2005 | +1                           | 1 (Mon)  |

👉 The **+1** for a leap year happens *after* the leap year itself, because 29 Feb inserts an extra day.

So in wer example, for 2503:

* Base anchor for 2500 would be **Sunday (0)**.
* 2501 → 1, 2502 → 2, 2503 → 3 (Wednesday).

That matches the full calculation we did!

---

**Subtraction Logic:**

Going **backward** in years is just the mirror of going forward — but we subtract instead of add (and we still have to watch for leap years).

Starting point: **Doomsday(2000) = 2 (Tuesday)**

To find **1999**:

1. Step back one year: subtract 1 → `2 − 1 = 1` (Monday).
2. Ask: was 2000 a leap year? (yes) → when we cross back *over* a leap year, we need to subtract one **more** day.

So:

$$
2 - 1 - 1 = 0 \quad (\text{Sunday})
$$

> **Doomsday(1999) = Sunday (0)**

✅ Rule of thumb:

* Going forward: +1 each year, +1 extra after a leap year.
* Going backward: −1 each year, −1 extra when we pass a leap year.

*(And remember: century years divisible by 400 are leap years; 2000 is, 1900 isn’t.)*
