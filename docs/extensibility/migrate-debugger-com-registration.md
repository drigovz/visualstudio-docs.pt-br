---
title: Migrar o registro de classe COM do depurador de 64 bits | Microsoft Docs
description: Saiba como registrar classes COM no msvsmon para extensões do depurador sem gravar no HKEY_CLASSES_ROOT.
ms.custom: SEO-VS-2020
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jmartens
ms.workload:
- greggm
ms.openlocfilehash: adc1db57de2167ff3caa0e87e1075c8ff5b462e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886711"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrar o registro de classe COM do depurador de 64 bits

Para extensões do depurador que registram classes COM em HKEY_CLASSES_ROOT usando regasm, regsvr32 ou gravando diretamente no registro e carregadas no *msvsmon.exe* (o depurador remoto), agora é possível fornecer esse registro para o msvsmon sem a necessidade de gravar no HKEY_CLASSES_ROOT. Isso afeta os avaliadores de expressão do depurador .NET herdados ou os mecanismos de depuração configurados para carregar no processo de *msvsmon.exe* .

## <a name="msvsmon-comclass-def"></a>msvsmon-ComClass-def

Para usar essa técnica, adicione um **.msvsmon-comclass-def.jsno* arquivo ao lado de msvsmon (installdir:* \Common7\IDE\Remote Debugger\x64 *).

Aqui está um exemplo de arquivo msvsmon-ComClass-def que registra uma classe gerenciada e uma nativa:

Nome do arquivo: *MyCompany.MyExample.msvsmon-comclass-def.jsem*

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
