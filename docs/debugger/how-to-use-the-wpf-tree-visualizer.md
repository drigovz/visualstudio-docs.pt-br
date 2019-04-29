---
title: 'Como: Usar o Visualizador de árvore do WPF | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da18990620644834192c38c24ced9a25ecb56215
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906103"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Como: Usar o visualizador de árvore do WPF
Você pode usar o visualizador de árvore do WPF para explorar a árvore visual de um objeto do WPF e exibir as propriedades de dependência do WPF para os objetos contidos nessa árvore. Para obter mais informações sobre árvores visuais, consulte [árvores no WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Para obter mais informações sobre propriedades de dependência, consulte [visão geral das propriedades de dependência](/dotnet/framework/wpf/advanced/dependency-properties-overview).

 Quando você abre o Visualizador de árvore do WPF, você verá dois painéis: o **árvore Visual** à esquerda e o **propriedades de** _nome_**:**  _Tipo_ painel à direita. Selecione qualquer objeto na **árvore Visual** painel e o **propriedades de** _nome_**:**_tipo_ é painel atualizado automaticamente para mostrar as propriedades desse objeto.

### <a name="to-open-the-wpf-tree-visualizer"></a>Para abrir o visualizador de árvore do WPF

1. Em uma DataTip, em uma janela **Inspeção**, **Autos** ou **Locais**, ao lado do nome do objeto do WPF, clique na seta adjacente ao ícone de lupa.

     Uma lista de visualizadores é exibida.

2. Clique em **Visualizador de árvore do WPF**.

### <a name="to-search-the-visual-tree"></a>Para pesquisar a árvore visual

- No painel **Árvore Visual**, digite a cadeia de caracteres que deseja pesquisar na caixa **Pesquisar**.

     O visualizador de árvore do WPF localiza imediatamente o primeiro objeto na árvore visual que corresponde à cadeia de caracteres digitada. Digite mais caracteres para localizar uma correspondência mais precisa.

    - Para ir para a próxima correspondência na árvore visual, clique em **Avançar**.

    - Para voltar à correspondência anterior, clique em **Ant**.

    - Para limpar os critérios de pesquisa, clique em **Limpar**.

### <a name="to-search-the-properties-list"></a>Para pesquisar a lista de propriedades

- No **propriedades de** _nome_**:**_tipo_ painel, digite a cadeia de caracteres que você deseja procurar no **filtrar**caixa.

     O visualizador de árvore do WPF localiza imediatamente as propriedades que correspondem à cadeia de caracteres digitada; agora, a lista exibe apenas as propriedades que correspondem à cadeia de caracteres digitada. Digite mais caracteres para localizar uma correspondência mais precisa.

    - Para limpar os critérios de pesquisa, clique em **Limpar**.

### <a name="to-close-the-visualizer"></a>Para fechar o visualizador

- Clique no ícone **Fechar** no canto superior direito da caixa de diálogo.

## <a name="see-also"></a>Consulte também
- [Criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)
- [Árvores no WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)
- [Visão geral das propriedades da dependência](/dotnet/framework/wpf/advanced/dependency-properties-overview)
