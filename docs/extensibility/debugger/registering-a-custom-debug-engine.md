---
title: Registrando um engine de depuração personalizado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe6fb916810bc8a7e960a4723a6a7c7a6f0c1410
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713219"
---
# <a name="register-a-custom-debug-engine"></a>Registre um mecanismo de depuração personalizado
O motor de depuração deve registrar-se como uma fábrica de classe, seguindo convenções COM, bem como registrar-se no Visual Studio através da subchave de registro do Visual Studio.

> [!NOTE]
> Você pode encontrar um exemplo de como registrar um mecanismo de depuração na amostra TextInterpreter, que é construído como parte do [Tutorial: Construindo um mecanismo de depuração usando ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24).

## <a name="dll-server-process"></a>Processo do servidor DLL
 Um mecanismo de depuração é normalmente configurado em seu próprio DLL como um servidor COM. Como tal, o motor de depuração deve registrar o CLSID de sua fábrica de classe com COM antes que o Visual Studio possa acessá-lo. Em seguida, o mecanismo de depuração deve registrar-se no Visual Studio para estabelecer quaisquer propriedades (também conhecidas como métricas) que o mecanismo de depuração suporta. A escolha das métricas escritas na subchave de registro do Visual Studio depende dos recursos que o mecanismo de depuração suporta.

 [Os auxiliares do SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) descrevem não apenas os locais de registro necessários para registrar um mecanismo de depuração; também descreve a biblioteca *dbgmetric.lib,* que contém uma série de funções úteis e declarações para desenvolvedores C++ que facilitam a manipulação do registro.

### <a name="example"></a>Exemplo
 O exemplo a seguir (da amostra TextInterpreter) mostra como usar a `SetMetric` função (de *dbgmetric.lib),* para registrar um mecanismo de depuração com o Visual Studio. As métricas que estão sendo passadas também são definidas em *dbgmetric.lib*.

> [!NOTE]
> TextInterpreter é um mecanismo básico de depuração; ele não configura — e, portanto, não registra — quaisquer outros recursos. Um motor de depuração mais `SetMetric` completo teria uma lista completa de chamadas ou seu equivalente, uma para cada recurso que o motor de depuração suporta.

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

## <a name="see-also"></a>Confira também
- [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Auxiliares SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Tutorial: Construindo um mecanismo de depuração usando ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)
