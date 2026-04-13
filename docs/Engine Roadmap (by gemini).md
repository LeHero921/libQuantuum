
# 🗺️ libQuantuum Engine Roadmap

## 🟦 Phase 1: Der Kern (The Backbone)

_Ziel: Ein stabiles Fenster und ein zentraler Zugriffspunkt für alle Systeme._

- [ ] **Application Wrapper:** Erstelle eine `Application`-Klasse, die `InitWindow()` und die Haupt-Loop verwaltet.
    
- [ ] **Engine Context / Service Locator:** Ein statischer Zugriffspunkt (z. B. `LQ::Core`), um von überall auf Audio, Physics und Renderer zuzugreifen.
    
- [ ] **Logger System:** Ein Utility, um Engine-Status und Fehler sauber in die Konsole zu schreiben.
    
- [ ] **Time Management:** Ein Wrapper für `GetFrameTime()`, der `deltaTime` und `totalTime` für alle Systeme bereitstellt.
    

## 🟨 Phase 2: Scene Management (The Flow)

_Ziel: Logische Trennung von Menüs, Levels und Ladebildschirmen._

- [ ] **Base Scene Class:** Virtuelle Klasse mit `OnEnter()`, `OnUpdate()`, `OnDraw()` und `OnExit()`.
    
- [ ] **Scene Manager:** System zum Wechseln von Szenen (`SwitchScene`) und zum sicheren Entladen der alten Daten.
    
- [ ] **First Test:** Implementiere eine `SplashScreen`- und eine `Game`-Szene, um den Wechsel zu testen.
    

## 🟧 Phase 3: Asset Management (The Resources)

_Ziel: Effizientes Laden von Daten ohne Duplikate im Speicher._

- [ ] **ResourceManager Template:** Ein System, das Texturen, Fonts und Sounds über einen `std::string` (Key) speichert.
    
- [ ] **Lazy Loading:** Assets werden nur geladen, wenn sie angefordert werden.
    
- [ ] **Auto-Cleanup:** Beim Szenenwechsel oder Beenden der Engine werden alle Instanzen automatisch entladen (`UnloadTexture`, etc.).
    

## 🟥 Phase 4: Entity & Object System (The Logic)

_Ziel: Das "MonoBehaviour"-Gefühl für Spielobjekte._

- [ ] **Entity Base Class:** Basis-Klasse mit Lifecycle-Methoden (`Start()`, `Update()`, `Destroy()`).
    
- [ ] **Transform Component:** Jedes Entity erhält standardmäßig Position, Rotation und Scale.
    
- [ ] **Object Manager:** Die Liste innerhalb einer Szene, die alle Entities verwaltet.
    
- [ ] **Safe Deletion:** Implementiere eine "Kill-List", damit Entities nicht mitten im Loop gelöscht werden (vermeidet Crashs).
    

## 🟪 Phase 5: Rendering Pipeline (The Visuals)

_Ziel: Sortiertes Zeichnen statt unkontrollierter Draw-Calls._

- [ ] **RenderCommand Struct:** Datenstruktur für Textur, Ziel-Rechteck, Layer und Z-Tiefe.
    
- [ ] **The Renderer:** Eine Klasse mit einer `Submit()`-Warteschlange.
    
- [ ] **Sorting Logic:** Implementiere `std::sort`, um die Commands nach Layer und Z-Tiefe (Y-Sort für Top-Down) zu ordnen.
    
- [ ] **Flush & Draw:** Die Methode, die am Ende des Frames alle sortierten Commands an Raylib übergibt.
    

## 🟩 Phase 6: Engine Systems (The Interaction)

_Ziel: Gameplay-Funktionen für die Entities._

- [ ] **Input Wrapper:** Vereinfachter Zugriff auf Tasten und Maus mit "Input Buffering" (z.B. `IsActionPressed("Jump")`).
    
- [ ] **Physics Bridge:** Ein einfaches AABB-System (Rechteck-Kollision) oder die Integration von Box2D.
    
- [ ] **Audio System:** Ein High-Level System, um Sounds über das Entity-System abzufeuern (`entity.PlaySound("boom")`).
    

## ⬜ Phase 7: Erweiterungen (The Polish)

_Ziel: Optimierung und Benutzerfreundlichkeit._

- [ ] **Hybrid ECS Integration:** Experimentiere damit, die Daten (Positionen/Sprites) in EnTT zu halten, während die Logik in den Entities bleibt.
    
- [ ] **UI System:** Ein Layer für Buttons und HUDs, der unabhängig von der Kamera-Position gerendert wird.
    
- [ ] **Scene Serialization:** Speichern und Laden von Szenen-Layouts über JSON oder XML.