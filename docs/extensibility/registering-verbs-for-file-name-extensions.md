---
title: Registrando verbos para extensões de nome de arquivo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac2854f1799075cc14d9beb557335be5228be21d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701526"
---
# <a name="register-verbs-for-file-name-extensions"></a>Registre verbos para extensões de nome de arquivo
A associação de uma extensão de nome de arquivo com um aplicativo geralmente tem uma ação preferida que ocorre quando um usuário clica duas vezes em um arquivo. Essa ação preferencial está ligada a um verbo, por exemplo, aberto, que corresponde à ação.

 Você pode registrar verbos associados a um identificador programático (ProgID) para uma extensão usando a tecla Shell localizada em **HKEY_CLASSES_ROOT\{progid}\shell**. Para obter mais informações, consulte [tipos de arquivo](/windows/desktop/shell/fa-file-types).

## <a name="register-standard-verbs"></a>Registre verbos padrão
 O sistema operacional reconhece os seguintes verbos padrão:

- Aberto

- Editar

- Reproduzir

- Imprimir

- Visualização

  Sempre que possível, registre um verbo padrão. A escolha mais comum é o verbo Aberto. Use o verbo Editar somente se houver uma diferença clara entre abrir o arquivo e editar o arquivo. Por exemplo, a abertura de um arquivo *.htm* exibe-o no navegador, enquanto a edição de um arquivo *.htm* inicia um editor HTML. Os verbos padrão são localizados com o local do sistema operacional.

> [!NOTE]
> Ao registrar verbos padrão, não defina o valor padrão para a tecla Abrir. O valor padrão contém a seqüência de exibição no menu. O sistema operacional fornece esta corda para verbos padrão.

 Os arquivos do projeto devem ser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] registrados para iniciar uma nova instância de quando um usuário abre o arquivo. O exemplo a seguir ilustra um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] verbo padrão de registro de um projeto.

```
[HKEY_CLASSES_ROOT\.csproj]
@="VisualStudio.csproj.8.0"

[HKEY_CLASSES_ROOT\.csproj\OpenWithList]
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]
@=""

[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]
"VisualStudio.csproj.8.0"=""

[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]
@="C# Project file"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""
```

 Para abrir um arquivo em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]uma instância existente de , registre uma chave DDEEXEC. O exemplo a seguir ilustra um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] registro de verbo padrão para um arquivo *.cs.*

```
[HKEY_CLASSES_ROOT\.cs]
@="VisualStudio.cs.8.0"

[HKEY_CLASSES_ROOT\.cs\OpenWithList]
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]
@=""

[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]
"VisualStudio.cs.8.0"=""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]
@="C# Source file"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]
@="Open(\"%1\")"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]
@="VisualStudio.8.0"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]
@="system"
```

## <a name="set-the-default-verb"></a>Defina o verbo padrão
 O verbo padrão é a ação que é executada quando um usuário clica duas vezes em um arquivo no Windows Explorer. O verbo padrão é o verbo especificado como o valor padrão para a **HKEY_CLASSES_ROOT\\chave*progid*\Shell.** Se nenhum valor for especificado, o verbo padrão será o primeiro verbo especificado na lista de tecla **HKEY_CLASSES_ROOT\\*progid*\Shell.**

> [!NOTE]
> Se você planeja alterar o verbo padrão para uma extensão em uma implantação lado a lado, considere o impacto na instalação e remoção. Durante a instalação, o valor padrão original é substituído.

## <a name="see-also"></a>Confira também
- [Gerenciar associações de arquivos lado a lado](../extensibility/managing-side-by-side-file-associations.md)
