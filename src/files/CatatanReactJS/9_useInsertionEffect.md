import { useInsertionEffect, useRef } from "react";

const StyledDivComponent = () => {
const elementRef = useRef(null);

useInsertionEffect(() => {
const element = elementRef.current;

    if (element) {
      // Menambahkan gaya dinamis sebelum proses layout dan rendering
      const dynamicStyle = document.createElement("style");
      dynamicStyle.textContent = `
        .custom-style {
          background-color: #add8e6;
          color: #00008b;
        }
      `;
      document.head.appendChild(dynamicStyle);

      // Menambahkan class ke elemen div
      element.classList.add("custom-style");

      return () => {
        // Menghapus gaya ketika komponen di-unmount
        document.head.removeChild(dynamicStyle);
      };
    }

}, []);

return (
<div ref={elementRef}>
This div has dynamically applied styles before layout.
</div>
);
};

export default StyledDivComponent;
