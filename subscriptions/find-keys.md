---
title: Encontrar e reivindicar chaves do produto (Product Keys) em assinaturas do Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: cabuschl
ms.assetid: da8df006-4896-4ff9-b487-698d78deabc3
ms.date: 07/30/2020
ms.topic: conceptual
description: Saiba como encontrar, reivindicar e exportar chaves do produto (Product Keys) em assinaturas do Visual Studio
ms.openlocfilehash: a246f66e429b78647f217468c7c19b703b419062
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2020
ms.locfileid: "91004961"
---
# <a name="finding-and-claiming-product-keys-in-visual-studio-subscriptions"></a>Encontrar e reivindicar chaves do produto (Product Keys) em assinaturas do Visual Studio
Este artigo explica como localizar, reivindicar e exportar chaves do produto (Product Keys) do https://my.visualstudio.com/productkeys.  Para saber mais sobre como ativar um produto com uma chave, versões de varejo e de licença de volume de chaves e limites diários de reivindicação de chaves do produto (Product Keys), acesse [visão geral das chaves do produto (Product Keys)](product-keys.md).

## <a name="locating-and-claiming-product-keys"></a>Localizando e solicitando chaves do produto (Product Keys)
Você deve estar conectado à sua assinatura do Visual Studio para exibir as chaves do produto (Product Keys). As chaves do produto individuais podem ser encontradas ao selecionar o link azul [Obter Chave](https://my.visualstudio.com/downloads) de um produto específico na página **Downloads** , conforme mostrado abaixo.  Todas as chaves também estão disponíveis agregadas na página [Chaves do Produto (Product Keys)](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs). Se existirem várias chaves para um único produto, serão exibidas observações na coluna Observações do download para ajudar você a identificar qual chave deve ser usada.
> [!div class="mx-imgBorder"]
> ![Obter chave da página de downloads](_img/product-keys/download-get-key.png "Selecione obter chave na página informações para qualquer download para obter uma chave para esse produto.")

Alguns produtos incluem diversas edições do produto em um único download. Nesses casos, a chave do produto (Product Key) informada determina qual edição é instalada.
Algumas chaves são fornecidas automaticamente, como as chaves “estáticas”, que você pode usar sempre que necessário, uma vez que não é preciso fazer a ativação. Outras chaves devem ser solicitadas ao selecionar o link **Obter Chave** do produto.

Vários tipos de chave estão disponíveis, de acordo com o produto.

### <a name="product-key-types"></a>Tipos de chave do produto (Product Key)

|    Tipo de Chave           |    Descrição                                                                                                                                                                                                           |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Não Aplicável                    |    Nenhuma chave é necessária para instalar este produto.                                                       |
|    Retail                     |    As chaves comerciais permitem várias ativações e são usadas para builds comerciais do produto. Em muitos casos, são permitidas 10 ativações por chave, embora normalmente sejam permitidas mais no mesmo computador.                                                       |
|    Ativação múltipla        |    Uma MAK (Chave de Ativação Múltipla) permite ativar várias instalações de um produto com a mesma chave. Normalmente, as MAKs são usadas com as versões de licenciamento por volume dos produtos. Geralmente, é fornecida somente uma chave MAK por assinatura.    |
|    Chave de ativação estática    |    As chaves de ativação estática são fornecidas para produtos que não exigem ativação. Elas podem ser usadas para um número ilimitado de instalações.                                                                                                                  |
|    Chave personalizada                 |    As chaves personalizadas permitem ações especiais ou fornecem informações para ativar ou instalar o produto.                                                                                                                                                                |
|    VA 1.0                     |    São chaves de ativação múltipla, semelhantes a uma MAK.                                                                                                                                                                                                 |
|    Chave OEM                    |    São chaves de fabricante de equipamento original que permitem ativações múltiplas.                                                                                                                                                                       |
|    Chave comercial do DreamSpark    |    Essas chaves comerciais destinam-se ao DreamSpark e permitem uma única ativação. As chaves comerciais do DreamSpark são emitidas em lotes e devem ser usadas principalmente por estudantes.                                                                                     |
|    Chave de laboratório do DreamSpark         |    Essas chaves para uso em laboratório destinam-se aos programas do DreamSpark e permitem ativações múltiplas. As chaves de laboratório do DreamSpark devem ser usadas em cenários de laboratórios de computadores de universidades.                                                                                       |
|    Chave MAK do DreamSpark         |    São chaves MAK para clientes do programa DreamSpark.                                                                                                                                                                                                  |
|

Você pode solicitar uma chave na página de download do produto ou pesquisar a chave que você precisa na página [Chaves do Produto (Product Keys)](https://my.visualstudio.com/productkeys).

### <a name="claiming-product-keys"></a>Solicitando chaves do produto (Product Keys)
Somente os assinantes com assinaturas ativas podem baixar produtos e solicitar chaves do produto (Product Keys).  Você poderá exportar as chaves solicitadas na página [Chaves do Produto (Product Keys)](https://my.visualstudio.com/productkeys) enquanto a assinatura estiver ativa.

Para solicitar a chave do produto (Product Key):
1. Entre na sua assinatura do Visual Studio.  Você deve estar conectado para baixar produtos ou solicitar chaves do produto (Product Keys).
2. Selecione a guia [chaves do produto](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) .
3. As chaves do produto (Product Keys) são listadas em ordem alfabética pelo nome do produto.  Você pode rolar para baixo até o nome do produto desejado ou pesquisá-lo usando a barra de pesquisa na parte superior da página.
> [!div class="mx-imgBorder"]
> ![Procurar a chave do produto (Product Key)](_img/product-keys/search-keys.png "Role até o produto desejado ou use a caixa de pesquisa para localizar rapidamente qualquer produto.")
   
Neste exemplo, utilizamos a barra de pesquisa para localizar uma chave do produto (Product Key) do Visual Studio Enterprise 2019.
Como é possível ver, há várias versões listadas.  Uma chave para cada um já foi reivindicada para o Visual Studio Enterprise 2019 versões 16.0 e 16.1.  Chaves adicionais de diferentes tipos ainda estão disponíveis para ambas as versões. Observe que é possível registrar uma breve observação sobre as chaves solicitadas na coluna **Observações** .  Você pode usar isso em conjunto com a data na coluna **Solicitada** para manter o controle das chaves já solicitadas.  Por exemplo, você pode fazer observações ao ativar uma instalação do produto usando a chave.

### <a name="exporting-your-claimed-keys"></a>Exportando as chaves solicitadas
Você pode exportar uma lista de todas as chaves já solicitadas, juntamente com uma grande seleção de chaves estáticas e de outros tipos automaticamente marcadas como “solicitadas” por você.

> [!IMPORTANT]
> Se sua assinatura expirar, você não poderá mais solicitar novas chaves nem exportar as chaves solicitadas.

Para exportar suas chaves, basta selecionar o link **exportar todas as chaves** na extrema direita da página chaves do produto (Product Keys).  Um arquivo .xml intitulado KeysExport.xml será criado e você terá a opção de abri-lo ou de salvá-lo.  Você precisará abrir o arquivo com um aplicativo compatível com arquivos .xml.  Por exemplo, você poderá abrir o arquivo como uma pasta de trabalho somente leitura no Excel.

## <a name="see-also"></a>Veja também
- [Documentação do Visual Studio](/visualstudio/)
- [Documentação do Azure DevOps](/azure/devops/)
- [Documentação do Azure](/azure/)
- [Documentação do Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Próximas etapas
Quando estiver pronto para baixar o software e usar as chaves, acesse https://my.visualstudio.com/downloads.  Para saber mais sobre como baixar software, confira a [visão geral de download](download-software.md).