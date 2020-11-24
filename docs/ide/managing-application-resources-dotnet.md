---
title: Gerenciar recursos do aplicativo (.NET)
description: Saiba como gerenciar os arquivos de recursos do aplicativo que não fazem parte do processo de compilação.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4707a3e33279ead458566bc01ed2eed8c67355cf
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596736"
---
# <a name="manage-application-resources-net"></a>Gerenciar recursos do aplicativo (.NET)

Arquivos de recurso são arquivos que fazem parte de um aplicativo, mas não são compilados, por exemplo, arquivos de ícone ou arquivos de áudio. Como esses arquivos não fazem parte do processo de compilação, você pode alterá-los sem precisar recompilar os binários. Se estiver planejando localizar seu aplicativo, você deverá usar arquivos de recurso para todas as cadeias de caracteres e outros recursos que precisam ser alterados ao localizar o aplicativo.

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Gerenciando recursos de aplicativo (Visual Studio para Mac)](/visualstudio/mac/managing-app-resources).

Para obter mais informações sobre os recursos em aplicativos .NET, consulte [recursos em aplicativos .net](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Trabalhar com recursos

Em um projeto de código gerenciado, abra a janela de propriedades do projeto. Você pode abrir a janela Propriedades das seguintes maneiras:

- Clicando com o botão direito do mouse no nó do projeto em **Gerenciador de soluções** e selecionando **Propriedades**
- Digitando **propriedades do projeto** na caixa de pesquisa **Ctrl**+**Q**
- Escolhendo **ALT** + **Enter** no **Gerenciador de soluções**

Selecione a guia **recursos** . Você pode adicionar um arquivo *. resx* se seu projeto não contiver um, adicionar e excluir diferentes tipos de recursos e modificar os recursos existentes.

## <a name="resources-in-other-project-types"></a>Recursos em outros tipos de projeto

Recursos são gerenciados de forma diferente em projetos do .NET que em outros tipos de projeto. Para obter mais informações sobre os recursos em:

- Aplicativos UWP (Plataforma Universal do Windows), consulte [Recursos do aplicativo e o Sistema de Gerenciamento de Recursos](/windows/uwp/app-resources/)
- Projetos C++, confira [trabalhar com arquivos de recurso](/cpp/windows/working-with-resource-files) e [Como criar um recurso](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Confira também

- [Recursos em aplicativos .NET (.NET Framework)](/dotnet/framework/resources/index)
- [Gerenciando recursos de aplicativo (Visual Studio para Mac)](/visualstudio/mac/managing-app-resources)
