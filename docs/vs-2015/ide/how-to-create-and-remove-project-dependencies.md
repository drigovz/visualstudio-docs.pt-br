---
title: Como criar e remover dependências do projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1403beccdb6bf9b938787f62cb3da2e5bb5c259
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668129"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Como criar e remover dependências de projeto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao compilar uma solução que contém vários projetos, pode ser necessário compilar determinados projetos primeiro, para gerar o código usado por outros projetos. Quando um projeto consome o código executável gerado por outro projeto, o projeto que gera o código é chamado de uma dependência de projeto do projeto que consome o código. Essas relações de dependência podem ser definidas na caixa de diálogo **dependências do projeto** .

### <a name="to-assign-dependencies-to-projects"></a>Para atribuir dependências a projetos

1. No Gerenciador de Soluções, selecione um projeto.

2. No menu **Projeto**, escolha **Dependências do Projeto**.

    A caixa de diálogo **Dependências do Projeto** é aberta.

   > [!NOTE]
   > A opção **Dependências do Projeto** está disponível apenas em uma solução com mais de um projeto.

3. Na guia **Dependências**, selecione um projeto no menu suspenso **Projeto**.

4. No campo **Depende de**, marque a caixa de seleção de qualquer outro projeto que deve ser compilado antes desse projeto.

   A solução deve consistir em mais de um projeto antes que seja possível criar dependências de projeto.

### <a name="to-remove-dependencies-from-projects"></a>Para remover dependências de projetos

1. No Gerenciador de Soluções, selecione um projeto.

2. No menu **Projeto**, escolha **Dependências do Projeto**.

     A caixa de diálogo **Dependências do Projeto** é aberta.

    > [!NOTE]
    > A opção **Dependências do Projeto** está disponível apenas em uma solução com mais de um projeto.

3. Na guia **Dependências**, selecione um projeto no menu suspenso **Projeto**.

4. No campo **Depende de**, desmarque as caixas de seleção ao lado de outros projetos que não são mais dependências desse projeto.

## <a name="see-also"></a>Consulte Também
 [Criando e limpando projetos e soluções no Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [compilando e criando](../ide/compiling-and-building-in-visual-studio.md) [entendendo configurações de compilação](../ide/understanding-build-configurations.md) [NIB como modificar propriedades de projeto e definições de configuração](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
