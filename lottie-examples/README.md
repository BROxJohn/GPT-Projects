# Exemple Lottie

Patru animatii Lottie scrise de mana (JSON / format Bodymovin), fara After Effects.
Sunt fisiere `.json` valide, compatibile cu `lottie-web`, `lottie-react`, Lottie iOS/Android
si lottiefiles.com.

## Continut

| Fisier | Animatie |
|---|---|
| `spinner.json` | Spinner circular care se roteste continuu (loop seamless) |
| `checkmark.json` | Cerc verde care apare cu "pop", apoi un checkmark alb care se deseneaza |
| `heart.json` | Inima rosie care pulseaza (scale) in bucla |
| `loading-dots.json` | Trei puncte care saltà secvential (efect "loading") |

Toate sunt 200x200 px, 60 fps.

## Cum le vezi

### Varianta 1 — pagina de preview inclusa
Deschide `index.html` intr-un browser (incarca `lottie-web` din CDN si afiseaza toate cele patru).
Daca browserul blocheaza fetch-ul local al fisierelor `.json`, porneste un server simplu:

```bash
cd lottie-examples
python3 -m http.server 8000
# apoi deschide http://localhost:8000
```

### Varianta 2 — lottiefiles.com
Urca oricare `.json` pe https://lottiefiles.com/ ca sa-l previzualizezi / editezi.

## Cum le folosesti in cod

### Web (lottie-web)
```html
<div id="anim" style="width:200px;height:200px"></div>
<script src="https://cdnjs.cloudflare.com/ajax/libs/bodymovin/5.12.2/lottie.min.js"></script>
<script>
  lottie.loadAnimation({
    container: document.getElementById('anim'),
    renderer: 'svg', loop: true, autoplay: true,
    path: 'spinner.json'
  });
</script>
```

### React (lottie-react)
```jsx
import Lottie from 'lottie-react';
import spinner from './spinner.json';

export default () => <Lottie animationData={spinner} loop />;
```

## Personalizare rapida
- **Culori**: campurile `c.k` sunt `[R, G, B, A]` cu valori 0..1 (ex. `[0.18, 0.45, 0.95, 1]` = albastru).
- **Viteza / durata**: `fr` = frame rate, `op` = ultimul frame. Mai mic `op` => animatie mai rapida.
- **Dimensiune**: `w` si `h` (canvas). Scalarea se face si din CSS pe container.
