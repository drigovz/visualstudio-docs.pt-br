---
title: 'Como: Adicionar um descritor de filtro a um método Finder | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bf1909f6c57ed82ba5afcfd30f6586e9bd4d6d14
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877764"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Como: Adicionar um descritor de filtro a um método Finder
  Descritores de filtro permitem que os clientes do modelo passar valores para métodos antes de serem executados. Para obter mais informações, consulte [criar um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Um cenário comum é que desejam que os usuários no SharePoint recuperar instâncias de um tipo de conteúdo externo que correspondem a certos critérios. Você pode dar suporte a esse cenário com a adição de um descritor de filtro a um método Finder.  
  
### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Para adicionar um descritor de filtro a um método Finder  
  
1.  No **detalhes do método BDC** janela, expanda o nó de um método Finder, expanda o **parâmetros** nó e, em seguida, adicione um parâmetro de entrada. Para obter mais informações, confira [Como: Adicionar um parâmetro a um método](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  No **detalhes do método** janela, escolha o descritor de tipo do parâmetro.  
  
3.  Na barra de menus, escolha **modo de exibição** > **janela propriedades**.  
  
4.  No **propriedades** janela, defina as **nome do tipo** propriedade para um tipo de dados que é apropriado para o filtro.  
  
     Por exemplo, um filtro pode usar uma data do pedido para limitar o número de pedidos de vendas retornado pelo método. Para dar suporte a esse filtro, o **nome do tipo** propriedade do descritor de tipo deve ser definida como **System. DateTime**.  
  
5.  No **detalhes do método** janela, expanda o **descritores de filtro** nó.  
  
6.  Na **adicionar um descritor de filtro** , escolha **criar descritor de filtro**.  
  
     Um novo descritor de filtro aparece sob o **descritores de filtro** nó.  
  
7.  Na barra de menus, escolha **modo de exibição** > **janela propriedades**.  
  
8.  No **propriedades** janela, escolha o **tipo** propriedade.  
  
9. Na lista que aparece para o **tipo** propriedade, escolha o padrão de filtragem que você deseja.  
  
     Por exemplo, para criar um filtro que usa uma data do pedido para limitar o número de pedidos de vendas retornados em um método Finder, escolha **comparação**. Um filtro de comparação garante que um método finder retorna apenas as instâncias que atendem a uma condição específica. Para obter mais informações sobre cada padrão de filtragem, consulte [tipos de filtros com suporte do BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
10. No **propriedades** janela, escolha o **descritores de tipo associados** propriedade.  
  
11. Na lista que aparece para o **descritores de tipo associados** propriedade, escolha o descritor de tipo que você criou anteriormente neste procedimento. Isso está relacionado o filtro para o parâmetro de entrada do método Finder.  
  
12. Adicione código ao método de localizador que retorna dados. Você pode usar o parâmetro de entrada como uma condição em uma consulta select.  
  
     O exemplo a seguir retorna as ordens de venda que têm a data do pedido especificado.  
  
    > [!NOTE]  
    >  Substitua o valor da `ServerName` campo com o nome do seu servidor.  
  
     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]  
  
## <a name="see-also"></a>Consulte também
 [Como: Adicionar um método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Como: Adicionar um método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Como: Adicionar um parâmetro a um método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Como: Definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Criar um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Integrando dados corporativos ao SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
