# Готовые тексты для GitHub

Скопируйте нужный раздел в соответствующие поля репозитория.

---

## 1. Описание репозитория (About / Repository description)

```
Самая маленькая графическая ОС с нуля: 16-битный загрузчик + 32-битное ядро, VESA 1024x768, окна, мышь и интернет-браузер. Загружается в QEMU.
```

Короткий вариант (до 100 символов):

```
Минимальная графическая ОС с нуля для QEMU: окна, мышь, интернет-браузер
```

## 2. Topics (теги)

```
operating-system osdev bootloader kernel qemu bare-metal vesa graphics browser assembly c tiny-os hobby-os
```

## 3. Commit message

```
Add bootable ISO and working internet browser

- Build El Torito no-emulation ISO with a CD-specific bootloader that
  copies the already-loaded kernel instead of calling int 13h (drive 0xE0)
- Add TINY BROWSER with URL bar, history, links, scrolling and compact
  HTML renderer; fetch real pages over COM1 via nethelper.py
- Fix mouse lag: redraw only two 12x16 rectangles on cursor movement
- Extend font to 83 glyphs, polish window chrome, icons and live RTC clock
```

Короткий вариант:

```
Add bootable ISO, internet browser and lag-free mouse rendering
```

## 4. Release notes (для Releases)

~~~markdown
## TINY OS v1.0 — первая публичная сборка

Самая маленькая графическая ОС, которую можно загрузить в QEMU.
Образ диска — всего 21 КБ.

### Что нового
- **TINY BROWSER**: адресная строка, история (BACK/GO), кликабельные ссылки,
  прокрутка и компактный HTML-рендерер. Страницы загружаются реально из
  интернета через `nethelper.py` (COM1 → UNIX socket → urllib).
- **Загрузочный ISO**: `tinyos.iso` грузится через `qemu-system-i386 -cdrom`.
- **Мышь без лагов**: при движении перерисовываются только два маленьких
  прямоугольника, а не весь экран.
- **Графика**: градиенты, скруглённые рамки окон, иконки, live-часы из CMOS.

### Файлы
- `os.img` — загрузочный raw-образ диска (21 КБ)
- `tinyos.iso` — загрузочный ISO (El Torito, no emulation)
- `run.sh` — запуск с интернетом (поднимает `nethelper.py`)

### Запуск
```bash
./run.sh                                             # с интернетом
qemu-system-i386 -cdrom tinyos.iso -boot d -m 64     # с ISO
```

### Управление
F5 — открыть браузер, ENTER — загрузить адрес, ↑/↓ — прокрутка,
BACK/GO — история/перезагрузка. Окна двигаются за заголовок.
~~~

## 5. Заголовок README (первая строка)

```
# TINY OS — самая маленькая графическая ОС с настоящим интернет-браузером
```

## 6. Шаблон issue (баг-репорт)

```
**Окружение:** QEMU <версия>, хост <ОС>, образ `os.img` / `tinyos.iso`
**Шаги:** ./run.sh → F5 → ввести URL → ENTER
**Ожидалось:** страница отображается
**Фактически:** ...
**Примечание:** без `run.sh` браузер показывает OFFLINE — это ожидаемо,
нужен хост-помощник `nethelper.py`.
```
