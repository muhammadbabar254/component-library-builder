const tabs = document.querySelectorAll(".tab");
const boxes = document.querySelectorAll(".box");

const textareas = document.querySelectorAll("textarea");

/* -------------------------
   TAB SWITCHING
--------------------------*/
tabs.forEach(tab => {
    tab.addEventListener("click", () => {

        // remove active from all tabs
        tabs.forEach(t => t.classList.remove("active"));
        tab.classList.add("active");

        // show correct box
        const target = tab.getAttribute("data-target");

        boxes.forEach(box => {
            box.classList.remove("active");
            if (box.id === target) {
                box.classList.add("active");
            }
        });
    });
});

/* -------------------------
   CLICK TO COPY CODE
--------------------------*/
textareas.forEach(area => {
    area.addEventListener("click", () => {

        area.select();
        document.execCommand("copy");

        const original = area.value;

        area.value = "Copied ✔";

        setTimeout(() => {
            area.value = original;
        }, 800);

    });
});