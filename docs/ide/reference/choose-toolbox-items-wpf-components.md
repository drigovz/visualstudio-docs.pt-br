---
title: Escolher Itens da Caixa de Ferramentas, Componentes WPF
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 731fe05e90e01c60f0a7ff3a14917d6d7625bc1e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75570551"
---
# <a name="choose-toolbox-items-wpf-components"></a>Escolher itens da Caixa de Ferramentas, Componentes do WPF

Essa guia da caixa de diálogo **Escolher Itens da Caixa de Ferramentas** exibe uma lista de controles do WPF (Windows Presentation Foundation) disponíveis no computador local. Para exibir essa lista, selecione **escolher itens de caixa de ferramentas** no menu **ferramentas** para exibir a caixa de diálogo **escolher itens de caixa de ferramentas** e, em seguida, selecione sua guia **componentes do WPF** . Para classificar os componentes listados, selecione qualquer título de coluna.

- Quando a caixa de seleção ao lado de um componente for selecionada, um ícone desse componente será exibido na **Caixa de ferramentas**.

    > [!TIP]
    > Para adicionar um controle WPF a um documento de projeto aberto para edição, arraste seu ícone **Caixa de ferramentas** para a superfície do modo de exibição de Design. Uma marcação e um código padrão do componente são inseridos no projeto, prontos para modificação. Para saber mais, confira [Caixa de Ferramentas](../../ide/reference/toolbox.md).

- Quando a caixa de seleção ao lado de um componente for desmarcada, o ícone correspondente será removido da **Caixa de Ferramentas**.

    > [!NOTE]
    > Os componentes .NET instalados no computador permanecem disponíveis independentemente de seus ícones serem exibidos na **Caixa de ferramentas**.

As colunas da guia **Componentes do WPF** contêm as seguintes informações:

**Nome**

Lista os nomes dos controles WPF para os quais existem entradas no Registro do computador.

**Namespace**

Exibe a hierarquia do namespace [API .NET](/dotnet/api/?view=netframework-4.7) que define a estrutura do componente. Classifique essa coluna para listar os componentes disponíveis em cada namespace .NET instalado no computador.

**Nome do assembly**

Exibe o nome do assembly .NET que inclui o namespace de cada componente. Classifique essa coluna para listar os namespaces contidos em cada assembly .NET instalado no computador.

**Diretório**

Exibe a localização do assembly .NET. O local padrão para todos os assemblies é o cachê global de assemblies. Para saber mais sobre o Cache de Assembly Global, confira [Trabalhar com assemblies e o Cache de Assembly Global](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).

## <a name="uielement-list"></a>Lista de UIElement

### <a name="filter"></a>Filtro

Filtra a lista de controles WPF com base na cadeia de caracteres fornecida na caixa de texto. Todas as correspondências de uma das quatro colunas são mostradas.

**Limpar**

Limpa a cadeia de caracteres de filtro.

**Procurar**

Abre a caixa de diálogo **Abrir**, que permite navegar para assemblies que contêm controles WPF. Use isso para carregar assemblies que não estão localizados no Cache de Assembly Global.

**Linguagem**

Mostra o idioma localizado do assembly que contém o controle WPF selecionado.

## <a name="limitations"></a>Limitações

A adição de um controle personalizado ou um <xref:System.Windows.Controls.UserControl> à caixa de ferramentas apresenta as seguintes limitações:

- Funciona somente para controles personalizados definidos fora do projeto atual.

- Não atualize corretamente ao alterar a configuração de solução de Depuração para Versão ou de Versão para Depuração. Isso ocorre porque a referência não é uma referência de projeto, mas refere-se ao assembly no disco. Se o controle fizer parte da solução atual, ao alterar de Depuração para Versão, o projeto continuará referenciando a versão de Depuração do controle.

Além disso, se os metadados em tempo de design são aplicados ao controle personalizado e esses metadados especificam que [Microsoft.Windows.Design.ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) é definido como `false`, o controle não é exibido na Caixa de Ferramentas.

É possível referenciar os controles diretamente no modo de exibição XAML, mapeando o namespace e o assembly do controle.

## <a name="see-also"></a>Veja também

- [Caixa de Ferramentas](../../ide/reference/toolbox.md)
- [Introdução ao WPF](../../designers/getting-started-with-wpf.md)
