# Быстрая настройка OpenHands

Этот файл содержит все необходимые команды и информацию для быстрой настройки и запуска OpenHands без использования GUI.

## 1. Создание файла конфигурации

Выполните эту команду в вашем терминале, чтобы создать файл `~/.openhands/settings.json` с вашими персональными настройками.

**Важно:** Замените `ВАШ_LLM_API_KEY` и `ВАШ_GITHUB_TOKEN` на ваши реальные значения.

```bash
mkdir -p ~/.openhands && echo '{
    "llm_model": "openai/gpt-4o",
    "llm_api_key": "ВАШ_LLM_API_KEY",
    "github_token": "ВАШ_GITHUB_TOKEN",
    "language": "uk",
    "enable_sound_notifications": true
}' > ~/.openhands/settings.json
```

### Объяснение параметров:

*   `"llm_model"`: Название модели, которую будет использовать OpenHands (например, `openai/gpt-4o`).
*   `"llm_api_key"`: Ваш ключ API для доступа к языковой модели.
*   `"github_token"`: Ваш токен GitHub для работы с репозиториями.
*   `"language"`: Язык интерфейса. `uk` — украинский.
*   `"enable_sound_notifications"`: Включает (`true`) или отключает (`false`) звуковые уведомления.

## 2. Запуск Docker-контейнера

После создания файла конфигурации используйте эту стандартную команду для запуска OpenHands. Она автоматически подхватит ваши настройки.

```bash
docker run -it --rm --pull=always \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v ~/.openhands:/.openhands \
    -p 3000:3000 \
    --add-host host.docker.internal:host-gateway \
    --name openhands-app \
    docker.all-hands.dev/all-hands-ai/openhands:0.44
```

## Источники информации (проанализированные файлы)

Эта инструкция была составлена на основе анализа следующих файлов в документации:

*   `docs/usage/llms/local-llms.mdx` (пример создания `settings.json`)
*   `docs/usage/configuration-options.mdx` (описание `config.toml` и переменных окружения)
*   `docs/openapi.json` (здесь было найдено свойство `enable_sound_notifications`)
*   `frontend/src/i18n/translation.json` (здесь был найден код для украинского языка — `uk`)
