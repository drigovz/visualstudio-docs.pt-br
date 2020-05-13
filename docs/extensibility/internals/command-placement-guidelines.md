---
title: Diretrizes de Colocação de Comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 021a5fd9f9931e3041a431d211c8ab49978bbbab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709565"
---
# <a name="command-placement-guidelines"></a>Diretrizes de posicionamento de comando
As práticas recomendadas para comandos de posicionamento no ambiente de desenvolvimento integrado (IDE) do Visual Studio variam dependendo do tamanho do conjunto de comandos. Os comandos são definidos e posicionados de acordo com as informações em arquivos *.vsct.*

## <a name="best-practices-for-all-command-sets"></a>Melhores práticas para todos os conjuntos de comandos
 Para cada conjunto de comandos, siga estas diretrizes:

- Prepare um gráfico da estrutura de comando com antecedência. Identifique os comandos, caixas de combinação, grupos de comando e menus de atalho que serão usados em mais de um local.

- Os comandos que aparecem no mesmo grupo devem estar relacionados.

- Grupos que contêm apenas um comando são aceitáveis.

- Os pacotes não devem adicionar muitos comandos aos menus existentes do Visual Studio. Em vez disso, eles devem criar menus ou submenus para hospedar os novos comandos.

- Quando você colocar um comando em um menu existente, nomeie o comando para que seu propósito seja claro e não seja confundido com os comandos existentes.

## <a name="best-practices-for-small-command-sets"></a>Melhores práticas para pequenos conjuntos de comandos
 Se você está desenvolvendo um VSPackage que tem apenas alguns comandos, siga também estas diretrizes:

- Quando possível, use o elemento [Pai](../../extensibility/parent-element.md) de um comando, caixa de combinação, grupo ou menu filho para colocá-lo no grupo apropriado.

- Atribuir esses grupos aos menus exibidos pelo VSPackage.

- O pai de um menu filho ou um comando deve ser um elemento [grupo.](../../extensibility/group-element.md) Atribuir comandos e menus de crianças a grupos e, em seguida, atribuir os grupos aos menus-pai.

- Você pode colocar um comando em grupos adicionais adicionando uma seção de elemento `CommandPlacements` [CommandPlacements](../../extensibility/commandplacements-element.md) após a definição do comando e, em seguida, adicionando ao elemento um elemento [CommandPlacement](../../extensibility/commandplacement-element.md) para cada grupo adicional.

## <a name="best-practices-for-large-command-sets"></a>Melhores práticas para grandes conjuntos de comandos
 Se o seu VSPackage terá muitos comandos que aparecerão em vários contextos, siga também essas diretrizes:

- Faça menus, grupos e comande a autoparentalidade. Ou seja, não atribua um `Parent` elemento na definição do item.

- Use `CommandPlacement` entradas de `CommandPlacements` elemento na seção elemento para colocar menus, grupos e comandos em seus menus e grupos-pai.

- Na `CommandPlacements` seção elemento, as entradas que povoam um determinado menu ou grupo devem ser adjacentes umas às outras. Isso ajuda a legibilidade e torna os `Priority` rankings mais fáceis de determinar.

## <a name="see-also"></a>Confira também
- [Como o VSPackages adiciona elementos de interface de usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Arquivos da tabela de comando do Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
