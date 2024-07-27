
# API: Module
### new Module(name, description, toggleable, category, callbacks)
Создает новый модуль.

### Параметры:
| Name        | Type                     | Description           |
|-------------|--------------------------|-----------------------|
| name        | string                   | Название модуля       |
| description | string                   | Описание модуля       |
| toggleable  | boolean                  | Возможность переключения |
| category    | ModuleCategory \| number | Категория модуля      |
| callbacks   | object                   | Объект колбэков       |

### Callbacks:
| Name    | Type     |
|---------|----------|
| onClick | function |

## Методы

### addSetting(setting)
Добавляет настройку.

#### Параметры:
| Name    | Type    |
|---------|---------|
| setting | Setting |

### getCategory()
Возвращает категорию.

#### Возвращает:
| Type                     | Description     |
|--------------------------|-----------------|
| Constants#ModuleCategory | category        |

### getDescription()
Возвращает описание.

#### Возвращает:
| Type   | Description   |
|--------|---------------|
| string | description   |

### getKeybind()
Возвращает клавишу привязки.

#### Возвращает:
| Type                    | Description |
|-------------------------|-------------|
| Constants#VK \| null    | keybind     |

### getName()
Возвращает название.

#### Возвращает:
| Type   | Description |
|--------|-------------|
| string | name        |

### getSetting(index)
Возвращает указанную настройку.

#### Параметры:
| Name  | Type   |
|-------|--------|
| index | number |

#### Возвращает:
| Type    | Description |
|---------|-------------|
| Setting | setting     |

### getSettings()
Возвращает все настройки.

#### Возвращает:
| Type         | Description |
|--------------|-------------|
| ArraySetting | settings    |

### hasSettings()
Проверяет наличие настроек.

#### Возвращает:
| Type    | Description     |
|---------|-----------------|
| boolean | has_settings    |

### isEnabled()
Проверяет включен ли модуль.

#### Возвращает:
| Type    | Description |
|---------|-------------|
| boolean | enabled     |

### isToggleable()
Проверяет можно ли переключать модуль.

#### Возвращает:
| Type    | Description   |
|---------|---------------|
| boolean | toggleable    |

### removeSetting(setting)
Удаляет настройку.

#### Параметры:
| Name    | Type    |
|---------|---------|
| setting | Setting |

### setKeybind(keybind)
Устанавливает привязку клавиши.

#### Параметры:
| Name    | Type      |
|---------|-----------|
| keybind | Constants#VK |

### toggle(enabled, notify)
Переключает состояние модуля.

#### Параметры:
| Name    | Type    |
|---------|---------|
| enabled | boolean |
| notify  | boolean |

 # API: Global
## Методы

### addTextToClipboard(text)
Копирует текст в буфер обмена.

#### Параметры:
| Name  | Type   |
|-------|--------|
| text  | string |

### getTextFromClipboard()
Возвращает текущий скопированный текст из буфера обмена.

#### Возвращает:
| Type   | Description    |
|--------|----------------|
| string | text           |

### isInGame()
Проверяет, находится ли локальный игрок в уровне (игре).

#### Возвращает:
| Type    | Description   |
|---------|---------------|
| boolean | Is playing?   |

### log(text)
Записывает текст в logs.txt.

#### Параметры:
| Name  | Type   |
|-------|--------|
| text  | string |

### notification(text)
Создает и отображает уведомление.

#### Параметры:
| Name  | Type   |
|-------|--------|
| text  | string |

### preventDefault()
Предотвращает выполнение хука.

### vkCodeToString(code)
Разрешает VK-код в строку.

#### Параметры:
| Name  | Type      |
|-------|-----------|
| code  | Constants#VK |

#### Возвращает:
| Type   | Description     |
|--------|-----------------|
| string | Resolved code   |
