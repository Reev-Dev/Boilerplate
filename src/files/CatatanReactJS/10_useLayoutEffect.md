import React, { useLayoutEffect, useRef } from 'react';

const LayoutEffectComponent = () => {
  const divRef = useRef(null);

  useLayoutEffect(() => {
    console.log('Height:', divRef.current.clientHeight);
  }, []);

  return (
    <div ref={divRef}>
      <p>This component logs its height after render.</p>
    </div>
  );
};

export default LayoutEffectComponent;