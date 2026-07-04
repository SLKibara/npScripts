// ==UserScript==
// @name         FEA - Active Pet First
// @namespace    https://github.com/SLKibara/npScripts/edit/Neopets-Scripts/FEA%20-%20Active%20Pet%20First
// @version      1.0
// @description  Move your active pet to the top of the Employment Agency pet list.
// @author       Kibara
// @match        https://www.neopets.com/faerieland/employ/employment.phtml?type=status
// @grant        none
// ==/UserScript==

(function () {
    'use strict';

    function getPairs(iter) {
        return [...iter].flatMap((_, i, a) =>
            i % 2 ? [] : [a.slice(i, i + 2)]
        );
    }

    // Active pet from the sidebar
    const activePet =
        document.querySelector(".sidebarHeader b")?.textContent.trim();

    if (!activePet) return;

    // Employment Status table
    const statusTable = [...document.querySelectorAll(".content table")]
        .find(t => t.textContent.includes("Current Job"));

    if (!statusTable) return;

    const tbody = statusTable.tBodies[0] || statusTable;

    for (const [header, pet] of getPairs(tbody.children)) {

        const petName = header.querySelector("b")?.textContent.trim();

        if (petName === activePet) {

            // Move the active pet pair to the top.
            tbody.prepend(pet);
            tbody.prepend(header);

            break;
        }
    }

})();
