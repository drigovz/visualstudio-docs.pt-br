---
title: Como criar várias configurações simultaneamente
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33cd217a08f62b4919af6d72017176c110cf5e5a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77904081"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Como criar várias configurações simultaneamente

É possível compilar a maioria dos tipos de projetos com várias, ou até mesmo todas, as configurações de build ao mesmo tempo usando a caixa de diálogo **Build em Lotes**. No entanto, não é possível compilar os seguintes tipos de projetos em várias configurações de build ao mesmo tempo:

1. Aplicativos [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] criados para Windows usando JavaScript.

2. Todos os projetos do Visual Basic.

Se uma solução contiver qualquer projeto desses dois tipos de projeto, então **batch build** não está disponível para essa solução. Nesse caso, o comando não aparece no menu **Build.**

   Para obter mais informações sobre configurações de build, consulte [Noções básicas sobre configurações de build](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Para compilar um projeto em várias configurações de build

1. Na barra de menu, escolha **Build** > **Batch Build**. Ou, **pressione Ctrl**+**Q** para abrir `Batch Build`a caixa de pesquisa e procurar .

2. Na coluna **Build**, marque as caixas de seleção para as configurações com as quais você deseja compilar um projeto.

    > [!TIP]
    > Para editar ou criar uma configuração de compilação para uma solução, escolha **'Build** > **Configuration Manager'** na barra de menus para abrir a caixa de diálogo Gerenciador de **configuração.** Depois de editar uma configuração de build para uma solução, escolha o botão **Recompilar** na caixa de diálogo **Build em Lotes** para atualizar todas as configurações de build dos projetos na solução.

3. Escolha os botões **Build** ou **Recompilar** para compilar o projeto com as configurações especificadas.

## <a name="see-also"></a>Confira também

- [Como criar e editar configurações](../ide/how-to-create-and-edit-configurations.md)
- [Compreender configurações de build](../ide/understanding-build-configurations.md)
- [Construa vários projetos em paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)