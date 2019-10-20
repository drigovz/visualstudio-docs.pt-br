---
title: Página Referências, Designer de Projeto (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
- Unused References dialog box
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8bb18ec8dd12431d650d844e3698c1986c8d8bd8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665637"
---
# <a name="references-page-project-designer-visual-basic"></a>Página Referências, Designer de Projeto (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use a página **Referências** do **Designer de Projeto** para gerenciar referências, referências Web e namespaces importados em seu projeto. Projetos podem conter referências a componentes COM, serviços Web XML, assemblies ou bibliotecas de classes do .NET Framework ou outras bibliotecas de classes. Para obter mais informações sobre o uso de referências, consulte [Gerenciando referências em um projeto](../../ide/managing-references-in-a-project.md).

 Para acessar a página **Referências**, escolha um nó de projeto (não o nó **Solução**) no **Gerenciador de Soluções**. Em seguida, escolha **Projeto**, **Propriedades** na barra de menus. Quando o Designer de Projeto for exibido, clique na guia **Referências**.

## <a name="uielement-list"></a>Lista UIElement
 As opções a seguir permitem selecionar ou remover referências e namespaces importados em seu projeto.

 **Referências não utilizadas** Clique neste botão para acessar a caixa de diálogo **referências não utilizadas** .

 A caixa de diálogo **Referências Não Utilizadas** permite remover referências que estão incluídas em seu projeto, mas na verdade não são usadas pelo código. Ela contém uma grade que lista o **Nome da Referência**, o **Caminho** e outras informações sobre as referências de namespace não utilizadas em seu projeto. Na grade, selecione as referências de namespace que você deseja remover de seu projeto e clique em **Remover**.

 **Caminhos de referência** Clique neste botão para acessar a caixa de diálogo **caminhos de referência** .

> [!NOTE]
> Quando o sistema do projeto encontra uma referência de assembly, o sistema resolve a referência examinando os seguintes locais, na seguinte ordem:
>
> 1. A pasta do projeto. Os arquivos da pasta do projeto aparecem no **Gerenciador de Soluções** quando **Mostrar Todos os Arquivos** não está em vigor.
>    2. Pastas especificadas na caixa de diálogo **Caminhos de Referência**.
>    3. Pastas que exibem arquivos na caixa de diálogo **Adicionar Referência**.
>    4. A pasta obj do projeto. (Quando você adiciona uma referência COM a seu projeto, um ou mais assemblies podem ser adicionados à pasta obj do projeto.)

 **Referências** do Esta lista mostra todas as referências no projeto, usadas ou não usadas.

 **Adicionar** Clique neste botão para adicionar uma referência ou referência Web à lista de **referências** .

 Escolha **Referência** para adicionar uma referência ao seu projeto usando a caixa de diálogo Adicionar Referência.

 Escolha **Referência Web** para adicionar uma referência Web ao seu projeto usando a caixa de diálogo Adicionar Referência Web.

 **Remover** Selecione uma ou mais referências na lista de **referências** e clique nesse botão para excluí-lo.

 **Atualizar referência Web** Selecione uma referência Web na lista **referências** e clique nesse botão para atualizá-la.

 **Namespaces importados** Você pode digitar seu próprio namespace nesta caixa e clicar em **Adicionar importação de usuário** para adicioná-lo à lista de namespaces.

 Você pode criar aliases para namespaces importados pelo usuário. Para fazer isso, digite o alias e o namespace no formato *alias*=*namespace*. Isso é útil se você estiver usando namespaces longos, por exemplo: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.

 **Adicionar importação de usuário** Clique neste botão para adicionar o namespace especificado na caixa **namespaces importados** à lista de namespaces importados. O botão fica ativo somente se o namespace especificado ainda não estiver na lista.

 **Lista de namespaces** Esta lista mostra todos os namespaces disponíveis. As caixas de seleção dos namespaces incluídos em seu projeto são selecionadas.

 **Atualizar importação de usuário** Selecione um namespace especificado pelo usuário na lista namespaces, digite o nome para o qual você deseja substituí-lo na caixa **namespaces importados** e, em seguida, clique neste botão para alterar para o novo namespace. O botão fica ativo somente se o namespace selecionado for aquele que você adicionou à lista usando o botão **Adicionar Importação de Usuário**. Você pode adicionar:

- Classes ou namespaces, como <xref:System.Math?displayProperty=fullName>.

- Importações com alias, como `VB=Microsoft.VisualBasic`.

- Namespaces XML, como `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.

## <a name="see-also"></a>Consulte também
 [NIB como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) [como: Adicionar ou remover namespaces importados (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md) [NIB: caixa de diálogo Adicionar referência da Web](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5) [instrução Imports (namespace XML)](https://msdn.microsoft.com/library/1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4)
