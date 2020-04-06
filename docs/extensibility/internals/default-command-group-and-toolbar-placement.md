---
title: Colocação padrão de comando, grupo e barra de ferramentas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b432b514231e876dda1393bad8a315030272d998
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708886"
---
# <a name="default-command-group-and-toolbar-placement"></a>Colocação padrão de comando, grupo e barra de ferramentas
Para a uniformidade e estabilidade do produto, a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface do ui exibe certos grupos de comando por padrão e fornece definições para comandos e grupos de comando. VsPackages também podem usar os comandos padrão e grupos de comando.

 Os grupos de comando padrão se enquadram em três categorias: comandos IDE, comandos de produto e comandos de editor.

## <a name="default-ide-commands"></a>Comandos IDE padrão
 A barra de ferramentas padrão do IDE inclui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]comandos compartilhados por todos os produtos contidos em . Estes incluem comandos relacionados a operações genéricas de projeto, como o comando **Salvar** e o comando **Adicionar item.** VsPackages não devem adicionar ou subtrair a esta barra de ferramentas, com uma exceção: Se o produto ou VSPackage adicionar uma nova janela de ferramenta, então a janela deve ser adicionada à lista de janelas de ferramentas disponíveis no menu **Exibir.** Novos produtos ou VSPackages podem adicionar sua própria barra de ferramentas.

## <a name="default-product-commands"></a>Comandos padrão do produto
 Cada produto pode fornecer ao IDE sua própria barra de ferramentas padrão que contém comandos importantes e frequentemente usados. No entanto, é melhor usar menus e barras de ferramentas existentes sempre que possível e suplementá-los com outras barras de ferramentas específicas da tarefa, conforme necessário.

 O campo prioritário para uma barra de ferramentas determina a colocação da linha. A prioridade zero coloca a barra de ferramentas na terceira linha (linha 3), abaixo da barra de menu (linha 1) e da **barra de** ferramentas Padrão (linha 2). Portanto, outras barras de ferramentas aparecem na linha (prioridade + 3). As barras de ferramentas subseqüentes são colocadas na mesma linha, se houver espaço; caso contrário, eles são automaticamente movidos para a próxima linha.

## <a name="default-editor-commands"></a>Comandos de editor padrão
 Um VSPackage que fornece um editor personalizado deve fornecer uma barra de ferramentas padrão que contenha os comandos mais importantes e usados com freqüência nesse editor. A barra de ferramentas do editor deve aparecer quando o editor estiver ativo e deve ser ocultada quando o editor não estiver ativo. Essa visibilidade é controlada `VisibilityConstraints` no elemento do arquivo *.vsct.*

 As barras de ferramentas do editor devem ser colocadas abaixo do IDE e das barras de ferramentas do produto.

## <a name="see-also"></a>Confira também
- [Comandos, menus e grupos definidos pelo IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Como o VSPackages adiciona elementos de interface de usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
