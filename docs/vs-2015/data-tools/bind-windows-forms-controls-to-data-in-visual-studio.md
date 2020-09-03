---
title: Associar controles do Windows Forms a dados
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a03f4df57b216fa68e5ac24df80b67917aa3e3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672982"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Associar controles do Windows Forms a dados no Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode exibir dados para os usuários do seu aplicativo ligando dados a Windows Forms. Para criar esses controles associados a dados, você pode arrastar itens da janela **fontes de dados** para o designer de formulários do Windows no Visual Studio. Este tópico descreve algumas das tarefas, ferramentas e classes mais comuns envolvidas na criação de aplicativos Windows Forms associados a dados.

 ![Operação de arrastar da fonte de dados](../data-tools/media/raddata-data-source-drag-operation.png "operação de arrastar da fonte de dados raddata")

 Para obter informações gerais sobre como criar controles vinculados a dados no Visual Studio, consulte [associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Para obter mais informações sobre associação de dados em Windows Forms, consulte [Windows Forms Associação de dados](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa).

## <a name="in-this-section"></a>Nesta seção

- [Associar controles do Windows Forms a dados](../data-tools/bind-windows-forms-controls-to-data.md)

- [Confirmar edições em processo em controles associados a dados antes de salvar os dados](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)

- [Criar tabelas de pesquisa em aplicativos do Windows Forms](../data-tools/create-lookup-tables-in-windows-forms-applications.md)

- [Criar um Windows Form para pesquisar dados](../data-tools/create-a-windows-form-to-search-data.md)

- [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados simples](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)

- [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados complexos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)

- [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados de consulta](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)

- [Passar dados entre formulários](../data-tools/pass-data-between-forms.md)

## <a name="bindingsource-component"></a>Componente BindingSource
 O <xref:System.Windows.Forms.BindingSource> componente atende a duas finalidades. Primeiro, ele fornece uma camada de abstração ao ligar os controles em seu formulário aos dados. Os controles no formulário são associados ao <xref:System.Windows.Forms.BindingSource> componente (em vez de serem vinculados diretamente a uma fonte de dados).

 Em segundo lugar, ele pode gerenciar uma coleção de objetos. Adicionar um tipo ao <xref:System.Windows.Forms.BindingSource> cria uma lista desse tipo.

 Para obter mais informações sobre o <xref:System.Windows.Forms.BindingSource> componente, consulte:

- [Componente BindingSource](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)

- [Visão geral do componente BindingSource](https://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)

- [Arquitetura do componente BindingSource](https://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)

## <a name="bindingnavigator-control"></a>Controle BindingNavigator
 Esse componente fornece uma interface do usuário para navegar pelos dados exibidos por um aplicativo do Windows. Para obter mais informações, consulte [Controle BindingNavigator](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

## <a name="datagridview-control"></a>Controle DataGridView
 Para exibir e editar dados tabulares de vários tipos diferentes de fontes de dados, use o <xref:System.Windows.Forms.DataGridView> controle. Você pode associar dados a um usando <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriedade. Para obter mais informações, consulte [visão geral do controle DataGridView](https://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488).

## <a name="see-also"></a>Consulte Também
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
