---
title: Escolher itens da caixa de ferramentas, componentes do WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c7967635d8e5d64907587fcd1a9b4d84a31d569
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660922"
---
# <a name="choose-toolbox-items-wpf-components"></a>Escolher Itens da Caixa de Ferramentas, Componentes WPF
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Essa guia da caixa de diálogo **Escolher Itens da Caixa de Ferramentas** exibe uma lista de controles do WPF (Windows Presentation Foundation) disponíveis no computador local. Para exibir essa lista, selecione **escolher itens de caixa de ferramentas** no menu **ferramentas** para exibir a caixa de diálogo **escolher itens de caixa de ferramentas** e, em seguida, selecione sua guia **componentes do WPF** . Para classificar os componentes listados, selecione qualquer título de coluna.

- Quando a caixa de seleção ao lado de um componente for selecionada, um ícone desse componente será exibido na **Caixa de ferramentas**.

  > [!TIP]
  > Para adicionar uma instância de um controle WPF a um documento de projeto aberto para edição, arraste seu ícone **Caixa de ferramentas** para a superfície do modo de exibição de Design. Uma marcação e um código padrão do componente são inseridos no projeto, prontos para modificação. Para obter mais informações, consulte [Como gerenciar a janela de ferramentas](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) e [Como manipular as guias da caixa de ferramentas](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

- Quando a caixa de seleção ao lado de um componente for desmarcada, o ícone correspondente será removido da **Caixa de ferramentas.**

  > [!NOTE]
  > Os componentes do .NET Framework instalados no computador permanecem disponíveis independentemente de seus ícones serem exibidos ou não na **Caixa de ferramentas**.

  As colunas da guia **Componentes do WPF** contêm as seguintes informações:

  Nome lista os nomes dos controles do WPF para os quais existem entradas no registro do seu computador.

  Namespace exibe a hierarquia do namespace da [biblioteca de classes NIB: .NET Framework](https://msdn.microsoft.com/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) que define a estrutura do componente. Classifique essa coluna para listar os componentes disponíveis em cada namespace do .NET Framework instalado no computador.

  Nome do assembly exibe o nome do assembly .NET Framework que inclui o namespace para cada componente. Classifique essa coluna para listar os namespaces contidos em cada assembly do .NET Framework instalado no computador.

  Diretório exibe o local do assembly .NET Framework. O local padrão para todos os assemblies é o cachê global de assemblies. Para obter mais informações sobre o Cache de Assembly Global, consulte [Trabalhando com assemblies e o cache de assembly global](https://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433).

## <a name="uielement-list"></a>Lista de elementos de interface do usuário
 **Filtrar** Filtra a lista de controles do WPF com base na cadeia de caracteres fornecida na caixa de texto. Todas as correspondências de uma das quatro colunas são mostradas.

 **Limpar** Limpa a cadeia de caracteres de filtro.

 **Procurar** Abre a caixa de diálogo **abrir** , que permite navegar até assemblies que contêm controles WPF. Use isso para carregar assemblies que não estão localizados no Cache de Assembly Global.

 **Idioma** do Mostra o idioma localizado do assembly que contém o controle WPF selecionado.

## <a name="limitations"></a>Limitações
 A adição de um controle personalizado ou um <xref:System.Windows.Controls.UserControl> à caixa de ferramentas apresenta as seguintes limitações.

- Funciona somente para controles personalizados definidos fora do projeto atual.

- Não atualize corretamente ao alterar a configuração de solução de Depuração para Versão ou de Versão para Depuração. Isso ocorre porque a referência não é uma referência de projeto, mas refere-se ao assembly no disco. Se o controle fizer parte da solução atual, ao alterar de Depuração para Versão, o projeto continuará referenciando a versão de Depuração do controle.

  Além disso, se os metadados de tempo de design forem aplicados ao controle personalizado e esses metadados especificarem que o [ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) está definido como `false` , o controle não aparecerá na caixa de ferramentas.

  É possível referenciar os controles diretamente no modo de exibição XAML, mapeando o namespace e o assembly do controle. Para obter mais informações, consulte [Como importar um namespace no XAML](https://msdn.microsoft.com/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).

## <a name="see-also"></a>Confira também

- [Caixa de diálogo Escolher Itens da Caixa de Ferramentas (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
- [Caixa de Ferramentas](../../ide/reference/toolbox.md)
- [Como usar um controle WPF de terceiros em um aplicativo WPF](https://msdn.microsoft.com/f4c0b601-3818-4f9f-85e5-77905f3b427f)
- [WPF Designer](https://msdn.microsoft.com/c6c65214-8411-4e16-b254-163ed4099c26)