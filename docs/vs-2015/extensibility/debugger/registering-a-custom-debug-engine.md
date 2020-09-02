---
title: Registrando um mecanismo de depuração personalizado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cf06e881034b980b8e40e095779007b3c7fa6f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703598"
---
# <a name="registering-a-custom-debug-engine"></a>Registrando um mecanismo de depuração personalizado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O mecanismo de depuração deve se registrar como uma fábrica de classes seguindo convenções COM, bem como registrar com o Visual Studio por meio da subchave do registro do Visual Studio.  
  
> [!NOTE]
> Um exemplo de como registrar um mecanismo de depuração pode ser encontrado no exemplo de textintérprete, que é criado como parte do [tutorial: Criando um mecanismo de depuração usando ATL com](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Processo do servidor DLL  
 Normalmente, um mecanismo de depuração é implementado em sua própria DLL como um servidor COM. Isso significa que o mecanismo de depuração deve registrar o CLSID de sua fábrica de classes com com, antes que o Visual Studio possa acessá-lo. Em seguida, o mecanismo de depuração deve se registrar no próprio Visual Studio para estabelecer quaisquer propriedades (também conhecidas como métricas) que o mecanismo de depuração suporta. A escolha das métricas que são gravadas na subchave do registro do Visual Studio para o mecanismo de depuração depende dos recursos aos quais o mecanismo de depuração dá suporte.  
  
 [Auxiliares de SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) descreve não apenas os locais de registro necessários para registrar um mecanismo de depuração; Ele também descreve a biblioteca dbgmetric. lib, que contém uma série de funções e declarações úteis para desenvolvedores de C++ que facilitam a manipulação do registro.  
  
### <a name="example"></a>Exemplo  
 Veja a seguir um exemplo típico (do exemplo de textintérprete) que mostra como usar a `SetMetric` função (de dbgmetric. lib) para registrar um mecanismo de depuração com o Visual Studio. As métricas que estão sendo passadas também são definidas em dbgmetric. lib.  
  
> [!NOTE]
> Textintérprete é um mecanismo de depuração básico; Ele não implementa — e, portanto, não se registra — quaisquer outros recursos. Um mecanismo de depuração mais completo teria uma lista completa de `SetMetric` chamadas ou seu equivalente, um para cada recurso compatível com o mecanismo de depuração.  
  
```  
// Define base registry subkey to Visual Studio.  
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";  
  
HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)  
{  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);  
  
    return base::RegisterServer(bRegTypeLib, pCLSID);  
}  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Auxiliares do SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: Criando um mecanismo de depuração usando o COM ATL](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)
