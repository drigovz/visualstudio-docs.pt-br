---
title: Registrando um personalizado de mecanismo de depuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 90400a9bf750eb80e40d6558fed382e18e7824ef
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316052"
---
# <a name="register-a-custom-debug-engine"></a>Registrar um mecanismo de depuração personalizado
O mecanismo de depuração deve se registrar como uma fábrica de classes, seguir as convenções de COM, bem como se registrar com o Visual Studio por meio da subchave do registro do Visual Studio.

> [!NOTE]
> Você pode encontrar um exemplo de como registrar um mecanismo de depuração em uma amostra TextInterpreter, que é criado como parte do [Tutorial: Criando um mecanismo de depuração usando COM ATL](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24).

## <a name="dll-server-process"></a>Processo do servidor DLL
 Um mecanismo de depuração normalmente é configurado em sua própria DLL como um servidor COM. Como tal, o mecanismo de depuração deve registrar o CLSID da sua fábrica de classe COM antes que o Visual Studio pode acessá-lo. Em seguida, o mecanismo de depuração deve ser registrado com o Visual Studio para estabelecer as propriedades (conhecido como métricas) de depuração dá suporte a do mecanismo. A escolha das métricas gravadas até a subchave de registro do Visual Studio depende dos recursos que o mecanismo de depuração suporta.

 [Auxiliares do SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) descreve não apenas os locais do Registro necessários para registrar um mecanismo de depuração; ele também descreve o *dbgmetric.lib* biblioteca, que contém um número de funções úteis e declarações para desenvolvedores de C++ que tornam a manipular o registro mais fácil.

### <a name="example"></a>Exemplo
 O exemplo a seguir (do exemplo TextInterpreter) mostra como usar o `SetMetric` função (de *dbgmetric.lib*) para registrar um mecanismo de depuração com o Visual Studio. As métricas que está sendo passadas também são definidas no *dbgmetric.lib*.

> [!NOTE]
> TextInterpreter é um mecanismo de depuração básica; ele não configurado – e, portanto, não registra — outros recursos. Um mecanismo de depuração mais completo teria uma lista completa de `SetMetric` chamadas ou seus equivalentes, uma para cada recurso, o mecanismo de depuração dá suporte.

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

## <a name="see-also"></a>Consulte também
- [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Auxiliares do SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Tutorial: Criando um mecanismo de depuração usando COM ATL](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)