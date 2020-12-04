---
title: Caixa de Ferramentas, Guia Dados
description: Saiba mais sobre os objetos de dados que você encontrará na guia dados da janela caixa de ferramentas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Toolbox, Data tab
- Data tab, Toolbox
- data [Visual Studio], Toolbox
ms.assetid: 2ae38b2a-29d2-461c-a67d-29dad274bf45
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78a697ae8d9f3f551c8bb734c28c1f53551b1f81
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96561078"
---
# <a name="toolbox-data-tab"></a>Caixa de ferramentas, guia Dados

Exibe objetos de dados que é possível adicionar a formulários e componentes. A guia **Dados** da **Caixa de Ferramentas** é exibida ao criar um projeto que tem um designer associado. A **Caixa de Ferramentas** é exibida por padrão no ambiente de desenvolvimento integrado do Visual Studio; se for preciso exibir a **Caixa de Ferramentas**, selecione **Caixa de Ferramentas** no menu **Exibir**.

> [!TIP]
> A execução do Assistente de Configuração de Fonte de Dados cria e configura automaticamente a maioria dos itens de dados. Para obter mais informações, consulte [Adicionar novas fontes de dados](../../data-tools/add-new-data-sources.md).

## <a name="ui-element-list"></a>Lista de elementos de interface do usuário

Para acessar diretamente a página de referência .NET de um componente, pressione **F1** no item na **Caixa de ferramentas** ou no item de componente na bandeja do designer.

|Nome|Descrição|
|----------|-----------------|
|<xref:System.Data.DataSet>|Adiciona uma instância de um conjunto de dados tipado ou não tipado ao formulário ou ao componente. Quando você arrasta esse objeto para um designer, ele exibe uma caixa de diálogo que permite selecionar uma classe de conjunto de dados tipado existente ou especificar se você deseja criar um conjunto de dados novo, em branco e não tipado. **Observação:** não use o objeto <xref:System.Data.DataSet> na **Caixa de Ferramentas** para criar um novo esquema e uma nova classe de conjunto de dados tipado. Para obter mais informações, consulte [Create and configure datasets (Criar e configurar conjuntos de dados)](../../data-tools/create-and-configure-datasets-in-visual-studio.md).|
|<xref:System.Windows.Forms.DataGridView>|Fornece uma maneira avançada e flexível para exibir dados em um formato de tabela.|
|<xref:System.Windows.Forms.BindingSource>|Simplifica o processo de associar controles a uma fonte de dados subjacente.|
|<xref:System.Windows.Forms.BindingNavigator>|Representa interface do usuário de navegação e a manipulação para controles em um formulário que está associado aos dados.|

## <a name="see-also"></a>Confira também

- [Acessar dados no Visual Studio](../../data-tools/accessing-data-in-visual-studio.md)
- [Ferramentas de dados do Visual Studio para .NET](../../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Ferramentas de conjunto de dados no Visual Studio](../../data-tools/dataset-tools-in-visual-studio.md)
- [Associar controles a dados no Visual Studio](../../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Associar controles do Windows Forms a dados no Visual Studio](../../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Editar dados em conjuntos de dados](../../data-tools/edit-data-in-datasets.md)
- [Validar dados em conjuntos de dados](../../data-tools/validate-data-in-datasets.md)
