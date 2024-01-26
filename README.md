# Introduktion till Git Flow

---

# Versionshantering med Git

- Versionshantering handlar om att **spara och spåra ändringar** i koden över tid.
- Git gör det möjligt att **spara olika versioner** av koden och **samarbeta** med andra.

---
# Vanlig git workflow

- **Klona** ett projekt från ett **Git-repository**.
- **Ändra** och **spara** koden lokalt.
- **Ladda upp** ändringarna till Git-repository.
  - git add .
  - git commit -m "Ändrade i koden"
  - git push
---
# Vad är grenar (Branches)?

- I Git är en **gren (branch)** en separat linje av kodutveckling.
- Grenar används för att **isolera och utveckla ändringar** utan att påverka huvudkoden.
- Efter att en ändring är klar i en gren, ska den **slås samman** med huvudgrenen.

---

# Git Flow-översikt

- **Git Flow** är en **arbetsflödesmodell** för att organisera och **hantera kodprojekt**.
- Huvudgrenar: **Main**, **Prod**, **Test**, **Dev**
- Funktionsgrenar (Feature branches)

---

# Standard uppställning av Git Flow

- **Main-grenen**: Huvudgren för **produktion**.
- **Prod-grenen**: Stabil version som används i **produktion**.
- **Test-grenen**: Används för att **testa nya funktioner** och buggfixar.
- **Dev-grenen**: Utvecklingsgren för **kommande funktioner**.
- **Funktionsgrenar**: Används för att **utveckla nya funktioner** eller göra **specifika ändringar**.
---

# Main- och Prod-grenar

- **Main-grenen**: Huvudgren för **produktion**.
- **Prod-grenen**: Stabil version som används i **produktion**.
- Separata grenar för att **säkerställa stabilitet** i produktionen.
- Grenarna ska vara **renade från onödig kod** efter Pull Request.

---

# Test- och Dev-grenar

- **Test-grenen**: Används för att **testa nya funktioner** och buggfixar.
- **Dev-grenen**: Utvecklingsgren för **kommande funktioner**.
- Skilja test- och utvecklingsmiljöer för att **undvika konflikter**.
- Grenarna ska **raderas efter att de är sammanfogade** i huvudgrenarna.

---

# Funktionsgrenar (Feature branches)

- **Funktionsgrenar** är användbara för att **utveckla nya funktioner** eller göra **specifika ändringar**.
- De isolerar ändringar från huvudgrenarna tills de är **klara**.
- Funktionsgrenar ska raderas efter att de är **slagna samman med huvudgrenen**.

---

# Planera ditt arbete

- **Planering** är nyckeln till **effektiv kodutveckling**.
- Skapa en **arbetsplan** för att **implementera nya funktioner** eller fixa buggar.

---

# Skapa och byta grenar

- Använd kommandon för att **skapa nya grenar** och **växla** mellan dem.
- Detta gör det enkelt att **organisera** och **jobba parallellt**.

---

# Fördelar

- **Git Flow** hjälper oss att **organisera och hantera** kodprojekt.
- Det är **enkelt** att **samarbeta** med andra utvecklare.
- Det är **enkelt** att **hantera ändringar** och **testa** nya funktioner.
- Om en ändring **misslyckas** kan vi **återgå** till en tidigare version.
- Vi kan **spara** och **spåra ändringar** i koden över tid.

---
# Nackdelar

- Git Flow kan vara **svårt att förstå** i början.
- Det kan vara **svårt att hantera** många grenar.
- Det kan vara **svårt att hantera** många Pull Requests.
- Bortglömda brancher kan **skapa förvirring**.
  (därför är det viktigt att radera brancher efter att de är slagna samman)
---
# Skydda grenar och Pull Requests

- **Grenskydd** är viktigt för att undvika oönskade ändringar.
- Använd **Pull Requests** för att **granska och godkänna ändringar** innan de slås samman.
- Ingen får ändra i grenar utan att **först skapa en Pull Request**.

---

# Exempel på Git Flow

- Låt oss titta på ett **visuellt exempel** av hur Git Flow fungerar med grenar och Pull Requests.

---

# Sammanfattning

- Vi har lärt oss om **Git Flow** och hur det hjälper oss att **hantera kodprojekt effektivt**.
- Använd Git Flow för att **förbättra din kodhantering** och **samarbete**.

---

# Skapa de olika grenarna

- Main grenen har vi från början
- Vi måste skapa grenarna i rätt ordning för att pull request ska fungera
- Skapa grenarna i följande ordning:
  - Prod
  - Test
  - Dev
  - Feature branches (skapas av kodarna själva)

---

# Exempel i konsolen
  
  ```bash
  git checkout -b prod
  git push --set-upstream origin prod
  git checkout -b test
  git push --set-upstream origin test
  git checkout -b dev
  git push --set-upstream origin dev
  ```
---
# Branch ordning

- main
- prod baseras på main
- test baseras på prod
- dev baseras på test
- feature branches baseras på dev

---

# Att tänka på

- **Main-grenen** ska **aldrig** ändras direkt
- **Prod-grenen** ska **aldrig** ändras direkt
- **Test-grenen** ska **aldrig** ändras direkt
- **Dev-grenen** ska helst **aldrig** inte direkt

---

# Uppdatera din dev innan du skapar en ny feature branch

- Innan du skapar en ny feature branch ska du alltid uppdatera din dev
- Detta gör du genom att byta till dev och köra följande kommandon
  ```bash
  git checkout dev
  git pull
  git checkout -b feature/ny-funktion
  ```
---

# Uppdatera din dev innan du skapar en pull request

- Innan du skapar en pull request ska du alltid merga din feature branch med dev
- Detta gör du med följande kommandon
  ```bash
  git checkout ny-funktion
  git add .
  git commit -m "Implementerade ny funktion"
  git checkout dev
  git pull
  git merge feature/ny-funktion
  ```
  Lös eventuella konflikter och pusha 
  Gör sedan en pull request från din feature branch till dev

---
# Efter pull request

När du raderat din branch på servern, ta bort den från din lokala dator med

```bash	
git remote prune origin
```
