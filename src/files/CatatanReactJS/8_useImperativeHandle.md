import { useRef, useImperativeHandle, forwardRef } from "react";

// eslint-disable-next-line react/display-name
const EnhancedInput = forwardRef((props, ref) => {
const internalRef = useRef();

useImperativeHandle(ref, () => ({
setFocus: () => {
internalRef.current.focus();
},
resetValue: () => {
internalRef.current.value = "";
},
}));

return <input ref={internalRef} {...props} />;
});

const ControlPanel = () => {
const enhancedInputRef = useRef();

return (
<div>
<button onClick={() => enhancedInputRef.current.setFocus()}>
Focus on Input
</button>
<button onClick={() => enhancedInputRef.current.resetValue()}>
Clear Input Value
</button>
<EnhancedInput
        ref={enhancedInputRef}
        placeholder="Type something here..."
      />
</div>
);
};

export default ControlPanel;
