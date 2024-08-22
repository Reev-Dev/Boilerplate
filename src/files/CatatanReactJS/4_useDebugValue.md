import { useDebugValue } from "react";

// Custom hook yang menggunakan useDebugValue untuk debugging
function useValueDebugger(input) {
useDebugValue(input > 10 ? "Above Threshold" : "Below Threshold");
return input;
}

const DebugInfo = () => {
const debuggedValue = useValueDebugger(12);

return (
<div>
<p>Current Value: {debuggedValue}</p>
</div>
);
};

export default DebugInfo;
