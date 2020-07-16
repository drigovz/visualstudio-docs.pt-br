---
title: 'IDebugProgram2:: execute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 676a3a7d184c1f34cafcfc2b2a4dd7a1c3f81a95
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387324"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Continua executando este programa a partir de um estado parado. Qualquer estado de execução anterior (como uma etapa) é limpo e o programa começa a ser executado novamente.  
  
> [!NOTE]
> Esse método é preterido. Em vez disso, use o método [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>Valor retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Quando o usuário inicia a execução de um estado parado em algum outro thread do programa, esse método é chamado neste programa. Esse método também é chamado quando o usuário seleciona o comando **Iniciar** no menu **depurar** no IDE. A implementação desse método pode ser tão simples quanto chamar o método [resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) no thread atual do programa.  
  
> [!WARNING]
> Não enviar um evento de interrupção ou um evento imediato (síncrono) para [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao lidar com essa chamada; caso contrário, o depurador pode parar de responder.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Circunstância](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Retomar](../../../extensibility/debugger/reference/idebugthread2-resume.md)
