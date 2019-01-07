---
title: 'Como: Exibir herança entre tipos (Designer de Classe)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.AssociationTypeNotFoundError
helpviewer_keywords:
- types [Visual Studio], inheritance
- types [Visual Studio], base
- types [Visual Studio], derived
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c7a9700996244d653f7a5ce32b78f4edd145d3f
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684477"
---
# <a name="how-to-view-inheritance-between-types-in-class-designer"></a>Como: Exibir herança entre tipos no Designer de Classe

Você poderá localizar a relação de herança, se ela existir, entre um tipo base e seus tipos derivados em um diagrama de classe no **Designer de Classe**. Para criar uma relação de herança, se nenhuma existir, entre dois tipos, confira [Como: Criar herança entre tipos](how-to-create-inheritance-between-types.md).

## <a name="to-find-the-base-type"></a>Para localizar o tipo base

1.  No diagrama de classe, clique no tipo para o qual você deseja ver a classe ou a interface base.

2.  No menu **Diagrama de Classe**, escolha **Mostrar Classe Base** ou **Mostrar Interfaces Base**.

     A classe ou a interface base do tipo aparece selecionada no diagrama. Todas as linhas de herança ocultas aparecem agora entre as duas formas.

Você pode também clicar com o botão direito do mouse no tipo cujo tipo base deseja exibir e escolher **Mostrar Classe Base** ou **Mostrar Interfaces Base**.

## <a name="to-find-the-derived-types"></a>Para localizar os tipos derivados

1.  No diagrama de classe, clique no tipo para o qual você deseja ver as classes ou interfaces derivadas.

2.  No menu **Diagrama de Classe**, escolha **Mostrar Classes Derivadas** ou **Mostrar Interfaces Derivadas**.

     As classes ou interfaces derivadas do tipo aparecem no diagrama. Todas as linhas de herança ocultas aparecem agora entre as formas.

Você pode também clicar com o botão direito do mouse no tipo cujos tipos derivados deseja ver e escolher **Mostrar Classes Derivadas** ou **Mostrar Interfaces Derivadas**.

## <a name="see-also"></a>Consulte também

- [Como: Criar associações entre tipos](how-to-create-associations-between-types.md)
- [Exibindo tipos e relações](designing-and-viewing-classes-and-types.md)