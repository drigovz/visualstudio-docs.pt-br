---
title: Adicionando switches de linha de comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f2df3a704c34d97c9d5acfa72249fe492b7f812
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740170"
---
# <a name="add-command-line-switches"></a>Adicionar interruptores de linha de comando
Você pode adicionar switches de linha de comando que se aplicam ao seu VSPackage quando *devenv.exe* é executado. Use <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> para declarar o nome do switch e suas propriedades. Neste exemplo, o switch MySwitch é adicionado para uma subclasse do VSPackage chamada **AddCommandSwitchPackage** sem argumentos e com o VSPackage carregado automaticamente.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 Os parâmetros nomeados são mostrados nas descrições a seguir.

||||
|-|-|-|-|
| Parâmetro | Descrição|
| Argumentos | O número de argumentos para a troca. Pode ser "*", ou uma lista de argumentos. |
| Carga de Demanda | Carregue o VSPackage automaticamente se isso estiver definido como 1, caso contrário definido como 0. |
| Helpstring | A seqüência de ajuda ou o ID de recurso da string a ser exibida com **devenv /?** |
| Nome | O interruptor. |
| PacoteGuid | O GUID do pacote. |

 O primeiro valor de Argumentos é geralmente 0 ou 1. Um valor especial de '*' pode ser usado para indicar que todo o restante da linha de comando é o argumento. Isso pode ser útil para depurar cenários onde um usuário deve passar em uma seqüência de comando dedepurador.

 O valor DemandLoad `true` é (1) ou `false` (0) indica que o VSPackage deve ser carregado automaticamente.

 O valor do HelpString é o ID de recurso da string que aparece no **devenv /?** Ajuda a exibir. Este valor deve estar na forma "#nnn" onde nnn é um inteiro. O valor da seqüência no arquivo de recursos deve terminar em um novo caractere de linha.

 O valor Nome é o nome do switch.

 O valor PackageGuid é o GUID do pacote que implementa este switch. O IDE usa este GUID para encontrar o VSPackage no registro ao qual o switch de linha de comando se aplica.

## <a name="retrieve-command-line-switches"></a>Recuperar switches de linha de comando
 Quando o pacote estiver carregado, você poderá recuperar os switches de linha de comando completando as etapas a seguir.

1. Na implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> seu `QueryService` VSPackage, ligue <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> para obter a <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interface.

2. Chamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> para recuperar os switches de linha de comando que o usuário inseriu.

   O código a seguir mostra como descobrir se o switch de linha de comando mySwitch foi inserido pelo usuário:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 É sua responsabilidade verificar os interruptores de linha de comando cada vez que seu pacote é carregado.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Opções de linha de comando do Devenv](../ide/reference/devenv-command-line-switches.md)
- [Utilitário CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)
- [. Arquivos Pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)
