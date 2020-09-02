---
title: OPTNAMECHANGEPFN | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4969dff811b6517c0274a35884703a9dc0c693cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194098"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa é uma função de retorno de chamada especificada em uma ligação para o [SccSetOption](../extensibility/sccsetoption-function.md) (usando a opção `SCC_OPT_NAMECHANGEPFN` ) e é usada para comunicar alterações de nome feitas pelo plug-in de controle do código-fonte de volta para o IDE.  
  
## <a name="signature"></a>Assinatura  
  
```cpp#  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 pvCallerData  
 no Valor de usuário especificado em uma chamada anterior para o [SccSetOption](../extensibility/sccsetoption-function.md) (usando a opção `SCC_OPT_USERDATA` ).  
  
 pszOldName  
 no O nome original do arquivo.  
  
 pszNewName  
 no O nome para o qual o arquivo foi renomeado.  
  
## <a name="return-value"></a>Valor Retornado  
 Nenhum.  
  
## <a name="remarks"></a>Comentários  
 Se um arquivo for renomeado durante uma operação de controle de origem, o plug-in de controle do código-fonte poderá notificar o IDE sobre a alteração do nome por meio desse retorno de chamada.  
  
 Se o IDE não oferecer suporte a esse retorno de chamada, ele não chamará o [SccSetOption](../extensibility/sccsetoption-function.md) para especificá-lo. Se o plug-in não oferecer suporte a esse retorno de chamada, ele retornará `SCC_E_OPNOTSUPPORTED` da `SccSetOption` função quando o IDE tentar definir o retorno de chamada.  
  
## <a name="see-also"></a>Consulte Também  
 [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
