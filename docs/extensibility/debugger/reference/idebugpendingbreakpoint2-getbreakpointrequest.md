---
description: "Gets the breakpoint request that was used to create this pending breakpoint."
title: IDebugPendingBreakpoint2::GetBreakpointRequest | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::GetBreakpointRequest
helpviewer_keywords:
- IDebugPendingBreakpoint2::GetBreakpointRequest method
- GetBreakpointRequest method
ms.assetid: cb1e36aa-4302-455c-98fb-6638a1ef5c46
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
---
# IDebugPendingBreakpoint2::GetBreakpointRequest

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Gets the breakpoint request that was used to create this pending breakpoint.

## Syntax

### [C#](#tab/csharp)
```csharp
int GetBreakpointRequest( 
   out IDebugBreakpointRequest2 ppBPRequest
);
```
### [C++](#tab/cpp)
```cpp
HRESULT GetBreakpointRequest( 
   IDebugBreakpointRequest2** ppBPRequest
);
```
---

## Parameters
`ppBPRequest`\
[out] Returns an [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) object representing the breakpoint request that was used to create this pending breakpoint.

## Return Value
 If successful, returns `S_OK`; otherwise, returns an error code. Returns `E_BP_DELETED` if the breakpoint has been deleted.

## See also
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
