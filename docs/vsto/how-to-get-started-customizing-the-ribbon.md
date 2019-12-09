---
title: 'Como: Introdução à personalização da faixa de faixas'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, adding Ribbon to project
- Ribbon [Office development in Visual Studio], adding
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, adding Ribbon to project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a9b0f1ef704f5dd1426374e23806e5950ed5f6bb
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255856"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Como: Introdução à personalização da faixa de faixas
  Para personalizar a faixa de visualização de um aplicativo Microsoft Office, adicione um item **da faixa de Ribbon (designer visual)** ou de **faixa (XML)** a um projeto do Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Para adicionar uma faixa de faixas a um projeto

1. No menu **projeto** , clique em **Adicionar novo item**.

2. Na caixa de diálogo **Adicionar novo item** , selecione **faixa de opções (designer visual)** ou **faixa de opções (XML)** . Para obter mais informações sobre esses modelos, consulte [visão geral da faixa](../vsto/ribbon-overview.md)de visualização.

3. Na caixa **nome** , digite um nome para o item da faixa de tipos.

    Os nomes não podem conter os seguintes caracteres:

   - Libra (#)

   - Percentual (%)

   - E comercial (&)

   - Asterisco (*)

   - Barra vertical (|)

   - Barra invertida (\\)

   - Dois pontos (:)

   - Aspas duplas (")

   - Menor que (\<)

   - Maior que (>)

   - Ponto de interrogação (?)

   - Barra (/)

   - Espaços à esquerda ou à direita (' ')

   - Nomes reservados para Windows ou DOS, como ("nul", "AUX", "con", "COM1", "LPT1" e assim por diante)

4. Clique em **OK**.

   O item da faixa de faixas aparece em **Gerenciador de soluções**. Para obter informações sobre as próximas etapas, consulte [visão geral da faixa](../vsto/ribbon-overview.md)de visualização.

## <a name="see-also"></a>Consulte também
- [Acessar a faixa de faixas em tempo de execução](../vsto/accessing-the-ribbon-at-run-time.md)
- [Designer da faixa de opções](../vsto/ribbon-designer.md)
- [XML da faixa de opções](../vsto/ribbon-xml.md)
- [Passo a passo: Criar uma guia personalizada usando o designer de faixa de faixas](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Passo a passo: Criar uma guia personalizada usando o XML da faixa de uma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
