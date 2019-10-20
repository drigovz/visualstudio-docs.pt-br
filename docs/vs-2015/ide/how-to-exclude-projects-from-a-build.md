---
title: Como excluir projetos de um build | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffa2b0fd8cab35fc73031d3ead8a5803558c2c07
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667952"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Como excluir projetos de um Build
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

É possível compilar uma solução sem compilar todos os projetos que ela contém. Por exemplo, é possível excluir um projeto que interrompe o build. É possível compilar o projeto depois de investigar e resolver os problemas.

 É possível excluir um projeto adotando as seguintes abordagens:

- Removê-lo temporariamente da configuração da solução ativa.

- Criar uma configuração da solução que não inclua o projeto.

  Para obter mais informações, consulte [Understanding Build Configurations (Noções básicas sobre configurações de build)](../ide/understanding-build-configurations.md).

### <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Para remover temporariamente um projeto da configuração da solução ativa

1. Na barra de menus, escolha **Build**, **Configuration Manager**.

2. Na tabela **Contextos do projeto**, localize o projeto que você deseja excluir do build.

3. Na coluna **Build** do projeto, desmarque a caixa de seleção.

4. Escolha o botão **Fechar** e, em seguida, recompile a solução.

### <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Para criar uma configuração da solução que exclui um projeto

1. Na barra de menus, escolha **Build**, **Configuration Manager**.

2. Na lista **Configuração da solução ativa**, escolha **\<Nova>** .

3. Na caixa **Nome**, insira um nome para a configuração da solução.

4. Na lista **Copiar configurações de**, escolha a configuração da solução na qual você deseja basear a nova configuração (por exemplo, **Depurar**) e, em seguida, escolha o botão **OK**.

5. Na caixa de diálogo **Configuration Manager**, desmarque a caixa de seleção na coluna **Build** do projeto que você deseja excluir e, em seguida, escolha o botão **Fechar**.

6. Na barra de ferramentas **Padrão**, verifique se a nova configuração da solução é a configuração ativa na caixa **Configurações da Solução**.

7. Na barra de menus, escolha **Compilar**, **Recompilar Solução**.

## <a name="see-also"></a>Consulte também
 [Noções básicas sobre configurações de compilação](../ide/understanding-build-configurations.md) [como criar e editar configurações](../ide/how-to-create-and-edit-configurations.md) [como: criar várias configurações simultaneamente](../ide/how-to-build-multiple-configurations-simultaneously.md)
