// ==UserScript==
// @name         Auto 2048 Game
// @namespace    http://your-namespace.com
// @version      1.0
// @description  Auto play 2048 game on specified website
// @match        https://twenty48.app/
// @grant        none
// ==/UserScript==

(function() {
    'use strict';

    // Функция для нажатия на кнопку
    function simulateKeyPress(keyCode) {
        var eventObj = document.createEventObject
            ? document.createEventObject()
            : document.createEvent("Events");
        
        if (eventObj.initEvent) {
            eventObj.initEvent("keydown", true, true);
        }

        eventObj.keyCode = keyCode;
        eventObj.which = keyCode;
        eventObj.ctrlKey = false;
        eventObj.shiftKey = false;
        eventObj.altKey = false;
        eventObj.metaKey = false;

        document.dispatchEvent(eventObj);
    }

    // Функция для автоматического прохождения игры
    function autoPlayGame() {
        setInterval(function() {
            // Здесь можно добавить логику для определения, какую кнопку нажимать
            // Например, можно использовать функцию simulateKeyPress с соответствующим кодом кнопки
            // Ниже приведен пример для нажатия кнопки влево (код кнопки: 37)
            simulateKeyPress(37);
        }, 1000); // Задержка между нажатиями в миллисекундах
    }

    // Запускаем автоматическое прохождение игры после загрузки страницы
    window.addEventListener('load', function() {
        autoPlayGame();
    });
})();
