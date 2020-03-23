---
title: Marca | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4bf89469c4137052247b5a1fdfee7f8dc694fbcc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773988"
---
# <a name="mark"></a>Marca
A opção *VSPerfCmd.exe* **Mark** insere as informações especificadas no arquivo de dados de criação de perfil. Marca pode ser listada em um relatório VSPerfReport separado ou na exibição de Relatório de marca da interface do usuário do criador de perfil. **Marca** pode ser usada para especificar os pontos inicial e final em relatórios e exibir filtros.

 A opção **Marca** deve ser a única opção especificada na linha de comando.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /Mark:MarkID,[MarkName]
```

#### <a name="parameters"></a>parâmetros
 `MarkID` Um inteiro definido pelo usuário que está listado como a ID de Marca em relatórios e exibições do criador de perfil. `MarkID` não precisa ser exclusivo.

 `MarkName` (Opcional) Uma cadeia de caracteres definida pelo usuário que está listada como o Nome da Marca em relatórios e exibições do criador de perfil. Se `MarkName` não for especificado, o campo Nome da marca da listagem de marca estará vazio. Coloque as cadeias de caracteres que contêm espaços ou barras ("/") entre aspas.

## <a name="example"></a>Exemplo
 Este exemplo insere uma marca com uma ID de 123 e o nome da marca de "TestMark".

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
VSPerfCmd.exe /Mark:123,TestMark
```

## <a name="see-also"></a>Confira também
- [Vsperfcmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
