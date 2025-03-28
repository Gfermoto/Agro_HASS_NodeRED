[
    {
        "id": "05d69f3ec5beea66",
        "type": "tab",
        "label": "🌿Рекомендации для газона",
        "disabled": false,
        "locked": true,
        "info": "",
        "env": []
    },
    {
        "id": "9b3ef29b7d5d34ed",
        "type": "inject",
        "z": "05d69f3ec5beea66",
        "name": "Ежедневно в 7:30",
        "props": [
            {
                "p": "payload"
            }
        ],
        "repeat": "",
        "crontab": "30 7 * * *",
        "once": false,
        "x": 200,
        "y": 100,
        "wires": [
            [
                "1cc743688e8ffe1d",
                "ee283a346718d6f1",
                "f74a1eb3081a39b2",
                "ed4814e57d36920d",
                "ac04c238b85a7dd8",
                "a35a910691a490ac",
                "dfcd74d02ef2905c",
                "e73fcb013d9eacf2"
            ]
        ]
    },
    {
        "id": "ed4814e57d36920d",
        "type": "http request",
        "z": "05d69f3ec5beea66",
        "name": "OpenMeteo Прогноз",
        "method": "GET",
        "ret": "txt",
        "url": "https://api.open-meteo.com/v1/forecast?latitude=55.934&longitude=36.61&daily=precipitation_sum,et0_fao_evapotranspiration,temperature_2m_min,temperature_2m_max&timezone=auto",
        "x": 200,
        "y": 200,
        "wires": [
            [
                "c5ac61376ffdaea3"
            ]
        ]
    },
    {
        "id": "c5ac61376ffdaea3",
        "type": "function",
        "z": "05d69f3ec5beea66",
        "name": "Парсинг OpenMeteo",
        "func": "try {\n  const data = JSON.parse(msg.payload);\n  const todayIndex = 0;\n  const tomorrowIndex = 1;\n  msg.openmeteo = {\n    // Данные на сегодня\n    rain_today: data.daily.precipitation_sum[todayIndex] || 0,\n    et0_today: data.daily.et0_fao_evapotranspiration[todayIndex] || 0,\n    temp_min_today: data.daily.temperature_2m_min[todayIndex] || 0,\n    temp_max_today: data.daily.temperature_2m_max[todayIndex] || 0,\n    // Данные на завтра\n    rain_tomorrow: data.daily.precipitation_sum[tomorrowIndex] || 0,\n    et0_tomorrow: data.daily.et0_fao_evapotranspiration[tomorrowIndex] || 0,\n    temp_min_tomorrow: data.daily.temperature_2m_min[tomorrowIndex] || 0,\n    temp_max_tomorrow: data.daily.temperature_2m_max[tomorrowIndex] || 0\n  };\n  msg.topic = 'openmeteo';\n} catch (error) {\n  msg.payload = { error: 'Ошибка запроса к Open-Meteo' };\n  msg.topic = 'openmeteo';\n}\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 440,
        "y": 200,
        "wires": [
            [
                "c40d8173ca320b56"
            ]
        ]
    },
    {
        "id": "1cc743688e8ffe1d",
        "type": "api-current-state",
        "z": "05d69f3ec5beea66",
        "name": "Влажность почвы",
        "server": "79fe7aa8.47ef74",
        "version": 3,
        "outputs": 1,
        "halt_if": "",
        "halt_if_type": "str",
        "halt_if_compare": "is",
        "entity_id": "sensor.gw2000a_soil_moisture_2",
        "state_type": "str",
        "blockInputOverrides": false,
        "outputProperties": [
            {
                "property": "payload",
                "propertyType": "msg",
                "value": "",
                "valueType": "entityState"
            },
            {
                "property": "data",
                "propertyType": "msg",
                "value": "",
                "valueType": "entity"
            }
        ],
        "for": 0,
        "forType": "num",
        "forUnits": "minutes",
        "x": 200,
        "y": 300,
        "wires": [
            [
                "99409fc073faaabf"
            ]
        ]
    },
    {
        "id": "99409fc073faaabf",
        "type": "change",
        "z": "05d69f3ec5beea66",
        "name": "topic: soil_moisture",
        "rules": [
            {
                "t": "set",
                "p": "topic",
                "pt": "msg",
                "to": "soil_moisture",
                "tot": "str"
            }
        ],
        "x": 440,
        "y": 300,
        "wires": [
            [
                "c40d8173ca320b56"
            ]
        ]
    },
    {
        "id": "ee283a346718d6f1",
        "type": "api-current-state",
        "z": "05d69f3ec5beea66",
        "name": "Температура почвы",
        "server": "79fe7aa8.47ef74",
        "version": 3,
        "outputs": 1,
        "halt_if_compare": "is",
        "entity_id": "sensor.gw2000a_soil_temperature_1",
        "state_type": "str",
        "blockInputOverrides": false,
        "outputProperties": [
            {
                "property": "payload",
                "propertyType": "msg",
                "value": "",
                "valueType": "entityState"
            },
            {
                "property": "data",
                "propertyType": "msg",
                "value": "",
                "valueType": "entity"
            }
        ],
        "for": 0,
        "forType": "num",
        "forUnits": "minutes",
        "x": 200,
        "y": 380,
        "wires": [
            [
                "a81377855cdd8317"
            ]
        ]
    },
    {
        "id": "a81377855cdd8317",
        "type": "change",
        "z": "05d69f3ec5beea66",
        "name": "topic: soil_temp",
        "rules": [
            {
                "t": "set",
                "p": "topic",
                "pt": "msg",
                "to": "soil_temp",
                "tot": "str"
            }
        ],
        "x": 440,
        "y": 380,
        "wires": [
            [
                "c40d8173ca320b56"
            ]
        ]
    },
    {
        "id": "f74a1eb3081a39b2",
        "type": "api-current-state",
        "z": "05d69f3ec5beea66",
        "name": "Осадки за день",
        "server": "79fe7aa8.47ef74",
        "version": 3,
        "outputs": 1,
        "halt_if_compare": "is",
        "entity_id": "sensor.ws2350_v2_37_daily_rain_rate",
        "state_type": "str",
        "blockInputOverrides": false,
        "outputProperties": [
            {
                "property": "payload",
                "propertyType": "msg",
                "value": "",
                "valueType": "entityState"
            },
            {
                "property": "data",
                "propertyType": "msg",
                "value": "",
                "valueType": "entity"
            }
        ],
        "for": 0,
        "forType": "num",
        "forUnits": "minutes",
        "x": 200,
        "y": 460,
        "wires": [
            [
                "d13cf5a1871a63c5"
            ]
        ]
    },
    {
        "id": "d13cf5a1871a63c5",
        "type": "change",
        "z": "05d69f3ec5beea66",
        "name": "topic: daily_rain",
        "rules": [
            {
                "t": "set",
                "p": "topic",
                "pt": "msg",
                "to": "daily_rain",
                "tot": "str"
            }
        ],
        "x": 440,
        "y": 460,
        "wires": [
            [
                "c40d8173ca320b56"
            ]
        ]
    },
    {
        "id": "ac04c238b85a7dd8",
        "type": "http request",
        "z": "05d69f3ec5beea66",
        "name": "OpenFarm API",
        "method": "GET",
        "ret": "txt",
        "url": "https://openfarm.cc/api/v1/crops?filter=lawn",
        "x": 200,
        "y": 600,
        "wires": [
            [
                "be11ce71bc30a698"
            ]
        ]
    },
    {
        "id": "be11ce71bc30a698",
        "type": "function",
        "z": "05d69f3ec5beea66",
        "name": "Парсинг OpenFarm",
        "func": "try {\n  const data = JSON.parse(msg.payload);\n  msg.topic = 'openfarm';\n  \n  // Стандартные рекомендации для газона\n  const defaultAdvice = {\n    watering: '1-2 раза в неделю, 10-15 л/м²',\n    fertilizing: 'NPK 20-5-10 весной и осенью',\n    mowing: '3-5 см',\n    description: 'Стандартные рекомендации по уходу за газоном'\n  };\n\n  if (data.data && data.data.length > 0) {\n    // Ищем запись о газоне\n    const lawnData = data.data.find(item => {\n      const name = item.attributes.name.toLowerCase();\n      const commonNames = item.attributes.common_names || [];\n      return name.includes('lawn') || \n             commonNames.some(n => n.toLowerCase().includes('lawn')) ||\n             name.includes('газон') ||\n             commonNames.some(n => n.toLowerCase().includes('газон'));\n    });\n\n    if (lawnData) {\n      msg.openfarm = {\n        watering: lawnData.attributes.watering || defaultAdvice.watering,\n        fertilizing: lawnData.attributes.fertilizing || defaultAdvice.fertilizing,\n        mowing: lawnData.attributes.mowing_height || defaultAdvice.mowing,\n        description: lawnData.attributes.description || defaultAdvice.description\n      };\n    } else {\n      msg.openfarm = defaultAdvice;\n    }\n  } else {\n    msg.openfarm = defaultAdvice;\n  }\n} catch (e) {\n  msg.topic = 'openfarm';\n  node.warn('Ошибка парсинга OpenFarm: ' + e);\n  // В случае ошибки используем стандартные рекомендации\n  msg.openfarm = {\n    watering: '1-2 раза в неделю, 10-15 л/м²',\n    fertilizing: 'NPK 20-5-10 весной и осенью',\n    mowing: '3-5 см',\n    description: 'Стандартные рекомендации по уходу за газоном'\n  };\n}\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 440,
        "y": 600,
        "wires": [
            [
                "c40d8173ca320b56"
            ]
        ]
    },
    {
        "id": "a35a910691a490ac",
        "type": "api-current-state",
        "z": "05d69f3ec5beea66",
        "name": "Влажность воздуха",
        "server": "79fe7aa8.47ef74",
        "version": 3,
        "outputs": 1,
        "halt_if_compare": "is",
        "entity_id": "sensor.ws2350_v2_37_humidity",
        "state_type": "str",
        "blockInputOverrides": false,
        "outputProperties": [
            {
                "property": "payload",
                "propertyType": "msg",
                "value": "",
                "valueType": "entityState"
            },
            {
                "property": "data",
                "propertyType": "msg",
                "value": "",
                "valueType": "entity"
            }
        ],
        "for": 0,
        "forType": "num",
        "forUnits": "minutes",
        "x": 160,
        "y": 540,
        "wires": [
            [
                "7b037fd413eeb4a5"
            ]
        ]
    },
    {
        "id": "dfcd74d02ef2905c",
        "type": "api-current-state",
        "z": "05d69f3ec5beea66",
        "name": "UV индекс",
        "server": "79fe7aa8.47ef74",
        "version": 3,
        "outputs": 1,
        "halt_if_compare": "is",
        "entity_id": "sensor.ws2350_v2_37_uv_index",
        "state_type": "str",
        "blockInputOverrides": false,
        "outputProperties": [
            {
                "property": "payload",
                "propertyType": "msg",
                "value": "",
                "valueType": "entityState"
            }
        ],
        "x": 150,
        "y": 660,
        "wires": [
            [
                "85a9010fc748339c"
            ]
        ]
    },
    {
        "id": "85a9010fc748339c",
        "type": "change",
        "z": "05d69f3ec5beea66",
        "name": "topic: uv",
        "rules": [
            {
                "t": "set",
                "p": "topic",
                "pt": "msg",
                "to": "uv",
                "tot": "str"
            }
        ],
        "x": 440,
        "y": 660,
        "wires": [
            [
                "c40d8173ca320b56"
            ]
        ]
    },
    {
        "id": "e73fcb013d9eacf2",
        "type": "api-current-state",
        "z": "05d69f3ec5beea66",
        "name": "Солнечная радиация",
        "server": "79fe7aa8.47ef74",
        "version": 3,
        "outputs": 1,
        "halt_if_compare": "is",
        "entity_id": "sensor.ws2350_v2_37_solar_radiation",
        "state_type": "str",
        "blockInputOverrides": false,
        "outputProperties": [
            {
                "property": "payload",
                "propertyType": "msg",
                "value": "",
                "valueType": "entityState"
            }
        ],
        "x": 160,
        "y": 700,
        "wires": [
            [
                "4eec93549956facb"
            ]
        ]
    },
    {
        "id": "4eec93549956facb",
        "type": "change",
        "z": "05d69f3ec5beea66",
        "name": "topic: solar",
        "rules": [
            {
                "t": "set",
                "p": "topic",
                "pt": "msg",
                "to": "solar",
                "tot": "str"
            }
        ],
        "x": 450,
        "y": 700,
        "wires": [
            [
                "c40d8173ca320b56"
            ]
        ]
    },
    {
        "id": "7b037fd413eeb4a5",
        "type": "change",
        "z": "05d69f3ec5beea66",
        "name": "topic: humidity",
        "rules": [
            {
                "t": "set",
                "p": "topic",
                "pt": "msg",
                "to": "humidity",
                "tot": "str"
            }
        ],
        "x": 440,
        "y": 540,
        "wires": [
            [
                "c40d8173ca320b56"
            ]
        ]
    },
    {
        "id": "c40d8173ca320b56",
        "type": "join",
        "z": "05d69f3ec5beea66",
        "name": "Объединение данных",
        "mode": "custom",
        "build": "object",
        "property": "payload",
        "propertyType": "msg",
        "key": "topic",
        "joiner": "",
        "joinerType": "str",
        "useparts": true,
        "accumulate": false,
        "timeout": "5",
        "count": "8",
        "reduceRight": false,
        "reduceExp": "",
        "reduceInit": "",
        "reduceInitType": "",
        "reduceFixup": "",
        "x": 790,
        "y": 140,
        "wires": [
            [
                "094f99bc2125e5e1",
                "5095aa5aa64054fb"
            ]
        ]
    },
    {
        "id": "094f99bc2125e5e1",
        "type": "function",
        "z": "05d69f3ec5beea66",
        "name": "Генерация советов",
        "func": "const soilMoisture = msg.payload.soil_moisture || 0;\nconst soilTemp = msg.payload.soil_temp || 0;\nconst dailyRain = msg.payload.daily_rain || 0;\nconst humidity = msg.payload.humidity || 0;\nconst openmeteo = msg.openmeteo || {\n  rain_today: 0, rain_tomorrow: 0,\n  temp_min_today: 0, temp_min_tomorrow: 0,\n  temp_max_today: 0, temp_max_tomorrow: 0,\n  et0_today: 0, et0_tomorrow: 0\n};\nconst openfarm = msg.openfarm || {};\n\nlet advice = [];\n\n// Проверка на заморозки по прогнозу OpenMeteo\nif (openmeteo.temp_min_today <= 0 || openmeteo.temp_min_tomorrow <= 0) {\n  const frostDays = [];\n  if (openmeteo.temp_min_today <= 0) {\n    frostDays.push('сегодня');\n  }\n  if (openmeteo.temp_min_tomorrow <= 0) {\n    frostDays.push('завтра');\n  }\n  advice.push(`❄️ **Внимание! Прогноз заморозков!** Минимальная температура воздуха: ${frostDays.join(' и ')} ${openmeteo.temp_min_today}°C и ${openmeteo.temp_min_tomorrow}°C`);\n}\n\n// Рекомендации по дренажу на основе осадков и влажности почвы (по датчикам)\nconst isWarmEnough = openmeteo.temp_min_today > 0 && openmeteo.temp_min_tomorrow > 0;\nif (isWarmEnough && (soilMoisture > 50 || dailyRain > 5)) {\n    let drainageReasons = [];\n    if (soilMoisture > 50) {\n        drainageReasons.push(`высокая влажность почвы (${soilMoisture}%)`);\n    }\n    if (dailyRain > 5) {\n        drainageReasons.push(`значительные осадки за день (${dailyRain} мм)`);\n    }\n    advice.push(`⚠️ **Дренаж**: Требуется. Причины: ${drainageReasons.join(', ')}`);\n}\nelse if (!isWarmEnough) {\n    advice.push('⚠️ **Дренаж**: Не рекомендуется из-за риска заморозков');\n}\n\n// Рекомендации по поливу с учетом всех параметров\nconst needsWatering = soilMoisture < 40 && // низкая влажность почвы (по датчику)\n  humidity < 70 && // низкая влажность воздуха (по датчику)\n  openmeteo.et0_today > 3 && // высокая испаряемость (прогноз)\n  openmeteo.rain_today < 5 && // нет значительных осадков сегодня (прогноз)\n  openmeteo.rain_tomorrow < 5; // нет значительных осадков завтра (прогноз)\n\nif (needsWatering) {\n  advice.push('💧 **Полив**: 10-15 л/м² до 10 утра');\n} else if (openmeteo.rain_today >= 5 || openmeteo.rain_tomorrow >= 5) {\n  const rainDays = [];\n  if (openmeteo.rain_today >= 5) {\n    rainDays.push('сегодня');\n  }\n  if (openmeteo.rain_tomorrow >= 5) {\n    rainDays.push('завтра');\n  }\n  advice.push(`💧 **Полив**: Не требуется, ожидаются осадки ${rainDays.join(' и ')}`);\n} else {\n  advice.push('💧 **Полив**: Не требуется, влажность почвы достаточная');\n}\n\n// Рекомендации по удобрениям на основе температуры почвы (по датчику)\nif (soilTemp > 5 && openmeteo.rain_today < 1 && openmeteo.rain_tomorrow < 1) {\n  advice.push('🌱 **Удобрения**: Внесите NPK 20-5-10 (30 г/м²)');\n} else if (soilTemp <= 5) {\n  advice.push('🌱 **Удобрения**: Не рекомендуется, температура почвы слишком низкая');\n}\n\n// Рекомендации по дренажу на основе осадков и влажности почвы (по датчикам)\nif (dailyRain > 10 || soilMoisture > 80) {\n  advice.push('⚠️ **Дренаж**: Проверьте низины');\n}\n\n// Рекомендации по стрижке на основе температуры почвы\nif (soilTemp > 5) {\n  advice.push(`✂️ **Стрижка**: ${openfarm.mowing || '3-5 см'}`);\n} else {\n  advice.push('✂️ **Стрижка**: Не рекомендуется, температура почвы слишком низкая');\n}\n\n// Добавляем общее описание состояния газона\nif (openfarm.description) {\n  advice.push(`ℹ️ ${openfarm.description}`);\n}\n\nmsg.payload = { advice: advice.join('\\n') || 'Сегодня особых действий не требуется.' };\nreturn msg;",
        "outputs": 1,
        "timeout": "",
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 1060,
        "y": 140,
        "wires": [
            [
                "ccc1b3db9e09ca7b"
            ]
        ]
    },
    {
        "id": "ccc1b3db9e09ca7b",
        "type": "function",
        "z": "05d69f3ec5beea66",
        "name": "Форматирование",
        "func": "const today = new Date().toLocaleDateString('ru-RU', { day: 'numeric', month: 'long' });\nconst text = `🌿 *Рекомендации на ${today}:*\\n${msg.payload.advice}`;\nmsg.payload = {\n  chatId: '-1001548038296',\n  type: 'message',\n  content: text,\n  parse_mode: 'Markdown'\n};\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 1070,
        "y": 220,
        "wires": [
            [
                "2fdf31d1eb667fc7",
                "2844a3b9c2962c52"
            ]
        ]
    },
    {
        "id": "2844a3b9c2962c52",
        "type": "telegram sender",
        "z": "05d69f3ec5beea66",
        "name": "Telegram",
        "bot": "df690a6504c1e710",
        "haserroroutput": false,
        "outputs": 1,
        "x": 1060,
        "y": 280,
        "wires": [
            []
        ]
    },
    {
        "id": "2fdf31d1eb667fc7",
        "type": "debug",
        "z": "05d69f3ec5beea66",
        "name": "debug 3",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "false",
        "statusVal": "",
        "statusType": "auto",
        "x": 1440,
        "y": 680,
        "wires": []
    },
    {
        "id": "5095aa5aa64054fb",
        "type": "function",
        "z": "05d69f3ec5beea66",
        "name": "Принятие решения о поливе",
        "func": "const soilMoisture = parseFloat(msg.payload.soil_moisture) || 0;\nconst humidity = parseFloat(msg.payload.humidity) || 0;\nconst dailyRain = parseFloat(msg.payload.daily_rain) || 0;\nconst uv = parseFloat(msg.payload.uv) || 0;\nconst solar = parseFloat(msg.payload.solar) || 0;\nconst openmeteo = msg.openmeteo || { \n  rain_today: 0, rain_tomorrow: 0,\n  et0_today: 0, et0_tomorrow: 0,\n  temp_min_today: 0, temp_min_tomorrow: 0\n};\n\n// Проверяем время начала полива (не раньше 6:00)\nconst now = new Date();\nconst currentHour = now.getHours();\nconst currentMinute = now.getMinutes();\n\n// Проверяем безопасные условия для полива\nconst isSafeTime = currentHour >= 6 && currentHour < 8; // Полив только с 6:00 до 8:00\nconst isSafeUV = uv < 2; // UV индекс должен быть меньше 2\nconst isSafeSolar = solar < 100; // Солнечная радиация должна быть меньше 100 Вт/м²\n\n// Проверяем условия для дренажа\nconst isWarmEnough = openmeteo.temp_min_today > 0 && openmeteo.temp_min_tomorrow > 0; // нет заморозков\nconst needsDrainage = isWarmEnough && ( // температура выше нуля И\n    soilMoisture > 50 || // высокая влажность почвы ИЛИ\n    dailyRain > 5 // значительные осадки за день\n);\n\n// Проверяем необходимость полива с учетом всех условий\nconst needsWatering = soilMoisture < 40 && // низкая влажность почвы\n                     humidity < 70 && // низкая влажность воздуха\n                     openmeteo.et0_today > 3 && // высокая испаряемость\n                     openmeteo.rain_today < 5 && // нет значительных осадков сегодня\n                     openmeteo.rain_tomorrow < 5 && // нет значительных осадков завтра\n                     isSafeTime && // безопасное время\n                     isSafeUV && // безопасный UV индекс\n                     isSafeSolar; // безопасная солнечная радиация\n\n// Расчет объема воды для полива (л/м²)\nlet wateringAmount = 0;\nif (needsWatering) {\n    // Базовый объем 10-15 л/м² с корректировкой на испаряемость\n    wateringAmount = 10 + Math.min(5, openmeteo.et0_today - 3);\n    \n    // Корректировка на влажность почвы\n    if (soilMoisture < 30) {\n        wateringAmount += 2; // Увеличиваем при очень сухой почве\n    } else if (soilMoisture > 35) {\n        wateringAmount -= 2; // Уменьшаем при почве ближе к нормальной\n    }\n    \n    // Учитываем прогноз осадков на сегодня\n    if (openmeteo.rain_today > 0 && openmeteo.rain_today < 5) {\n        wateringAmount -= openmeteo.rain_today; // Уменьшаем на объем ожидаемых осадков\n    }\n    \n    // Ограничиваем минимальное и максимальное значение\n    wateringAmount = Math.max(8, Math.min(17, wateringAmount));\n}\n\n// Общий объем для всей площади (300 кв.м)\nconst totalWateringAmount = wateringAmount * 300;\n\n// Сохраняем целевой объем воды и время начала полива\nglobal.set('watering_target_volume', totalWateringAmount);\nglobal.set('watering_start_time', new Date().getTime());\n\n// Добавляем информацию о причинах отказа от полива\nconst reasons = [];\nif (!isSafeTime) {\n    reasons.push(`Время полива не подходящее (${currentHour}:${currentMinute})`);\n}\nif (!isSafeUV) {\n    reasons.push(`UV индекс слишком высокий (${uv})`);\n}\nif (!isSafeSolar) {\n    reasons.push(`Солнечная радиация слишком высокая (${solar} Вт/м²)`);\n}\n\nmsg.payload = { needsWatering: needsWatering, needsDrainage: needsDrainage, wateringAmountPerSqm: wateringAmount, totalWateringAmount: totalWateringAmount, area: 300, soilMoisture: soilMoisture, humidity: humidity, dailyRain: dailyRain, et0Today: openmeteo.et0_today, rainToday: openmeteo.rain_today, rainTomorrow: openmeteo.rain_tomorrow, uv: uv, solar: solar, currentTime: `${currentHour}:${currentMinute}`, safetyReasons: reasons };\n\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 830,
        "y": 320,
        "wires": [
            [
                "8c9507b620c6de95"
            ]
        ]
    },
    {
        "id": "8c9507b620c6de95",
        "type": "switch",
        "z": "05d69f3ec5beea66",
        "name": "Решение о поливе/дренаже",
        "property": "payload.needsDrainage",
        "propertyType": "msg",
        "rules": [
            {
                "t": "true"
            },
            {
                "t": "true",
                "v": "payload.needsWatering",
                "vt": "msg"
            },
            {
                "t": "else"
            }
        ],
        "checkall": "false",
        "outputs": 3,
        "x": 780,
        "y": 440,
        "wires": [
            [
                "6d1c6d5715a7ba64"
            ],
            [
                "7ccd53e93596cb2b"
            ],
            [
                "c01b169c9b6aeb1a"
            ]
        ]
    },
    {
        "id": "6d1c6d5715a7ba64",
        "type": "function",
        "z": "05d69f3ec5beea66",
        "name": "Логирование необходимости дренажа",
        "func": "const reasons = [];\n\n// Определяем причины необходимости дренажа\nif (msg.payload.soilMoisture > 50) {\n    reasons.push(`высокая влажность почвы (${msg.payload.soilMoisture}%)`);\n}\n\nif (msg.payload.dailyRain > 5) {\n    reasons.push(`значительные осадки за день (${msg.payload.dailyRain} мм)`);\n}\n\n// Форматируем дату\nconst now = new Date();\nconst formattedDate = now.toLocaleDateString('ru-RU');\n\nmsg.payload = {\n    content: `💧 *Требуется дренаж ${formattedDate}*\\n` +\n             `Причины: ${reasons.join('; ')}`\n};\n\nnode.status({fill:\"yellow\", shape:\"ring\", text:\"Требуется дренаж\"});\n\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 740,
        "y": 760,
        "wires": [
            [
                "2fdf31d1eb667fc7"
            ]
        ]
    },
    {
        "id": "7ccd53e93596cb2b",
        "type": "api-call-service",
        "z": "05d69f3ec5beea66",
        "name": "Запуск полива",
        "server": "79fe7aa8.47ef74",
        "version": 7,
        "debugenabled": false,
        "action": "rest_command.wfc01_watering_start",
        "floorId": [],
        "areaId": [],
        "deviceId": [],
        "entityId": [],
        "labelId": [],
        "data": "",
        "dataType": "json",
        "mergeContext": "",
        "mustacheAltTags": false,
        "outputProperties": [],
        "queue": "none",
        "blockInputOverrides": false,
        "domain": "rest_command",
        "service": "wfc01_watering_start",
        "x": 1140,
        "y": 340,
        "wires": [
            [
                "1a530f792347289c"
            ]
        ]
    },
    {
        "id": "1a530f792347289c",
        "type": "api-current-state",
        "z": "05d69f3ec5beea66",
        "name": "Мониторинг расхода воды",
        "server": "79fe7aa8.47ef74",
        "version": 3,
        "outputs": 1,
        "halt_if": "",
        "halt_if_type": "str",
        "halt_if_compare": "is",
        "entity_id": "sensor.wfc01_water_total",
        "state_type": "str",
        "blockInputOverrides": false,
        "outputProperties": [
            {
                "property": "payload",
                "propertyType": "msg",
                "value": "",
                "valueType": "entityState"
            }
        ],
        "x": 1140,
        "y": 440,
        "wires": [
            [
                "f4cddc1eb58ebe21"
            ]
        ]
    },
    {
        "id": "f4cddc1eb58ebe21",
        "type": "function",
        "z": "05d69f3ec5beea66",
        "name": "Проверка объема воды",
        "func": "// Получаем текущий объем воды из датчика\nconst currentVolume = parseFloat(msg.payload) || 0;\n\n// Получаем целевой объем и начальный объем\nconst targetVolume = global.get('watering_target_volume') || 0;\nlet startVolume = global.get('watering_start_volume');\nlet startTime = global.get('watering_start_time');\n\n// Если начальный объем еще не установлен, устанавливаем его сейчас\nif (startVolume === undefined || startVolume === null) {\n    startVolume = currentVolume;\n    startTime = new Date().getTime();\n    global.set('watering_start_volume', startVolume);\n    global.set('watering_start_time', startTime);\n    node.status({fill:\"blue\", shape:\"dot\", text:\"Начало полива\"});\n}\n\n// Рассчитываем выданный объем воды\nconst deliveredVolume = currentVolume - startVolume;\n\n// Проверяем на ошибки\nif (deliveredVolume < 0) {\n    node.error(\"Ошибка: отрицательный объем воды\");\n    return [null, null];\n}\n\n// Проверяем время полива (максимум 2 часа)\nconst now = new Date().getTime();\nconst wateringDuration = (now - startTime) / 60000; // в минутах\nconst maxDuration = 120; // 2 часа в минутах\n\n// Проверяем условия для остановки полива\nconst targetReached = deliveredVolume >= targetVolume;\nconst timeExceeded = wateringDuration >= maxDuration;\n\n// Рассчитываем прогресс полива в процентах\nconst progressPercent = targetVolume > 0 ? Math.min(100, (deliveredVolume / targetVolume) * 100) : 0;\n\n// Сохраняем текущий прогресс для отображения\nglobal.set('watering_progress', progressPercent.toFixed(0));\nglobal.set('watering_delivered', deliveredVolume.toFixed(0));\n\n// Обновляем статус ноды с более подробной информацией\nnode.status({\n    fill: \"blue\",\n    shape: \"dot\",\n    text: `Прогресс: ${progressPercent.toFixed(0)}%, ${deliveredVolume.toFixed(0)}л из ${targetVolume.toFixed(0)}л, ${Math.round(wateringDuration)} мин`\n});\n\n// Если достигли целевого объема или превысили время, останавливаем полив\nif (targetReached || timeExceeded) {\n    msg.targetReached = targetReached;\n    msg.timeExceeded = timeExceeded;\n    msg.deliveredVolume = deliveredVolume;\n    msg.progressPercent = progressPercent;\n    msg.wateringDuration = Math.round(wateringDuration);\n    return [msg, null];\n} else {\n    // Продолжаем мониторинг\n    msg.targetReached = false;\n    msg.timeExceeded = false;\n    msg.deliveredVolume = deliveredVolume;\n    msg.progressPercent = progressPercent;\n    msg.wateringDuration = Math.round(wateringDuration);\n    return [null, msg];\n}",
        "outputs": 2,
        "noerr": 0,
        "x": 1410,
        "y": 440,
        "wires": [
            [
                "2fb9c4c7f5063bfc"
            ],
            [
                "9f33ec9292f1315f"
            ]
        ]
    },
    {
        "id": "9f33ec9292f1315f",
        "type": "delay",
        "z": "05d69f3ec5beea66",
        "name": "Проверка каждые 30 сек",
        "pauseType": "delay",
        "timeout": "30",
        "timeoutUnits": "seconds",
        "rate": "1",
        "nbRateUnits": "1",
        "rateUnits": "second",
        "randomFirst": "1",
        "randomLast": "5",
        "randomUnits": "seconds",
        "drop": false,
        "allowrate": false,
        "outputs": 1,
        "x": 1250,
        "y": 540,
        "wires": [
            [
                "1a530f792347289c"
            ]
        ]
    },
    {
        "id": "2fb9c4c7f5063bfc",
        "type": "api-call-service",
        "z": "05d69f3ec5beea66",
        "name": "Остановка полива",
        "server": "79fe7aa8.47ef74",
        "version": 7,
        "debugenabled": false,
        "action": "rest_command.wfc01_watering_stop",
        "floorId": [],
        "areaId": [],
        "deviceId": [],
        "entityId": [],
        "labelId": [],
        "data": "",
        "dataType": "json",
        "mergeContext": "",
        "mustacheAltTags": false,
        "outputProperties": [],
        "queue": "none",
        "blockInputOverrides": false,
        "domain": "rest_command",
        "service": "wfc01_watering_stop",
        "x": 1410,
        "y": 340,
        "wires": [
            [
                "6ae93e004a8bcbde"
            ]
        ]
    },
    {
        "id": "6ae93e004a8bcbde",
        "type": "function",
        "z": "05d69f3ec5beea66",
        "name": "Логирование завершения полива",
        "func": "// Получаем данные о поливе\nconst startTime = global.get('watering_start_time');\nconst deliveredVolume = msg.deliveredVolume || 0;\nconst targetVolume = global.get('watering_target_volume') || 0;\nconst wateringDuration = msg.wateringDuration || 0;\n\n// Определяем причину остановки полива\nlet stopReason = '';\nif (msg.targetReached) {\n    stopReason = 'достигнут целевой объем воды';\n} else if (msg.timeExceeded) {\n    stopReason = 'превышено максимальное время полива (2 часа)';\n} else {\n    stopReason = 'неизвестная причина';\n}\n\n// Форматируем дату и время\nconst now = new Date();\nconst formattedDate = now.toLocaleDateString('ru-RU');\nconst formattedTime = now.toLocaleTimeString('ru-RU');\n\n// Процент от целевого объема\nconst percentDelivered = targetVolume > 0 ? (deliveredVolume / targetVolume) * 100 : 100;\n\nmsg.payload = {\n    content: `✅ *Полив завершен ${formattedDate} в ${formattedTime}*\\n` +\n             `Причина: ${stopReason}\\n` +\n             `Длительность: ${wateringDuration} мин\\n` +\n             `Выдано воды: ${deliveredVolume.toFixed(0)} л (${percentDelivered.toFixed(0)}% от плана)\\n` +\n             `Расход: ${(deliveredVolume / 300).toFixed(1)} л/м²`\n};\n\n// Очищаем глобальные переменные после завершения\nglobal.set('watering_start_time', null);\nglobal.set('watering_target_volume', null);\nglobal.set('watering_start_volume', null);\nglobal.set('watering_progress', null);\nglobal.set('watering_delivered', null);\n\nnode.status({fill:\"green\", shape:\"ring\", text:\"Полив завершен\"});\n\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 1420,
        "y": 240,
        "wires": [
            [
                "2fdf31d1eb667fc7"
            ]
        ]
    },
    {
        "id": "c01b169c9b6aeb1a",
        "type": "function",
        "z": "05d69f3ec5beea66",
        "name": "Логирование отказа от полива",
        "func": "const reasons = [];\n\n// Определяем причины отказа от полива\nif (msg.payload.soilMoisture >= 40) {\n    reasons.push(`Влажность почвы достаточная (${msg.payload.soilMoisture}%)`);\n}\n\nif (msg.payload.rainToday >= 5) {\n    reasons.push(`Ожидаются осадки сегодня (${msg.payload.rainToday} мм)`);\n}\n\nif (msg.payload.rainTomorrow >= 5) {\n    reasons.push(`Ожидаются осадки завтра (${msg.payload.rainTomorrow} мм)`);\n}\n\nif (msg.payload.et0Today <= 3) {\n    reasons.push(`Низкая испаряемость (ET0: ${msg.payload.et0Today})`);\n}\n\n// Добавляем причины, связанные с безопасностью\nif (msg.payload.safetyReasons && msg.payload.safetyReasons.length > 0) {\n    reasons.push(...msg.payload.safetyReasons);\n}\n\n// Форматируем дату\nconst now = new Date();\nconst formattedDate = now.toLocaleDateString('ru-RU');\n\nmsg.payload = {\n    content: `ℹ️ *Полив ${formattedDate} не требуется*\\n` +\n             `Причины: ${reasons.join('; ')}`\n};\n\nnode.status({fill:\"blue\", shape:\"ring\", text:\"Полив не требуется\"});\n\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 910,
        "y": 700,
        "wires": [
            [
                "2fdf31d1eb667fc7"
            ]
        ]
    },
    {
        "id": "7b95d3b38e7a0ad1",
        "type": "catch",
        "z": "05d69f3ec5beea66",
        "name": "",
        "scope": null,
        "uncaught": false,
        "x": 950,
        "y": 600,
        "wires": [
            [
                "2fdf31d1eb667fc7"
            ]
        ]
    },
    {
        "id": "79fe7aa8.47ef74",
        "type": "server",
        "name": "Home Assistant",
        "addon": true,
        "rejectUnauthorizedCerts": true,
        "ha_boolean": "",
        "connectionDelay": false,
        "cacheJson": false,
        "heartbeat": false,
        "heartbeatInterval": "",
        "statusSeparator": "",
        "enableGlobalContextStore": false
    },
    {
        "id": "df690a6504c1e710",
        "type": "telegram bot",
        "botname": "KPMG_TG_Bot",
        "usernames": "",
        "chatids": "2093488216, -1001548038296",
        "baseapiurl": "",
        "testenvironment": false,
        "updatemode": "polling",
        "pollinterval": "2500",
        "usesocks": false,
        "sockshost": "",
        "socksprotocol": "socks5",
        "socksport": "6667",
        "socksusername": "anonymous",
        "sockspassword": "",
        "bothost": "",
        "botpath": "",
        "localbothost": "",
        "localbotport": "8443",
        "publicbotport": "8443",
        "privatekey": "",
        "certificate": "",
        "useselfsignedcertificate": false,
        "sslterminated": false,
        "verboselogging": false
    }
]