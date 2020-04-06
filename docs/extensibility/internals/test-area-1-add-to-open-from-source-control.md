---
title: 'Área de teste 1: adicionar para abrir do controle de origem | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ac7b8e5a60fe25ac22272cc28fc3ed6f903b058
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704673"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Área de teste 1: Adicionar/abrir do controle de origem
Esta área de teste plug-in de controle de origem abrange colocar soluções ou projetos sob controle de origem e recuperá-los do controle de origem.

## <a name="command-menu-access"></a>Acesso ao menu de comando
 Os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seguintes caminhos de menu de ambiente de desenvolvimento integrado são usados nos casos de teste:

- Para [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], aberto a partir do controle de origem: **Arquivo**, **Aberto**, Solução **de projeto;**/**Solution** olhar no [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] local.

- Para outros plug-ins de controle de origem, abra a partir do controle de origem: **Arquivo,** **Controle de origem,** **Abertura do Controle de Código**.

- Adicionar ao controle de origem: **Arquivo,** **Controle de origem,** **adicionar solução ao arquivo de controle de fonte,** **controle de origem,** **adicionar projetos selecionados ao controle de origem**.

- Menu de atalho (Projeto/Solução), **Adicionar solução ao controle de origem**.

- Adicionar a partir do controle de origem: **Arquivo,** **Controle de origem,** **adicionar projeto do controle de origem**.

- Para [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], adicionar a partir do controle de origem também está disponível a partir de **File**, **Add**, **Projeto existente;** olhar no [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] local.

  > [!NOTE]
  > Um caminho de um arquivo local ou um IIS local (servidor web) pode ser usado neste teste.

## <a name="expected-behavior"></a>Comportamento esperado

- Para cada tipo de projeto suportado, um usuário deve ser capaz de "Adicionar" e "Abrir a partir" controle de origem.

- Quando um projeto é adicionado ao \<Controle de Origem, um arquivo *ProjectName*>.vspscc correspondente (arquivo de dica do projeto) é criado. Ele contém lista de arquivos de exclusão e informações de conexão. Não exclua este arquivo porque ele contém informações específicas para o projeto.

- Quando uma solução é adicionada ao \<controle de origem, um arquivo *correspondente SolutionName*>.vssscc (triplo S) é criado. O arquivo de texto contém informações de conexão e uma lista de arquivos de exclusão, semelhante ao arquivo de dica do projeto. Este arquivo é temporário e existe apenas no banco de dados de controle de origem.

- Quando uma solução é aberta \<a partir do controle de origem, um arquivo *SolutionName*>.vsscc (double S) que existe apenas no banco de dados de controle de origem, é criado localmente em um arquivo temporário. Este arquivo contém o caminho da pasta de conexão de solução para o arquivo de solução. Este arquivo é temporário e a cópia local é excluída quando a operação "Abrir do Controle de Código" for concluída.

- Depois que um projeto é adicionado ao controle de origem, você pode executar qualquer ação de controle de origem nele (Check out, Get, e assim por diante).

## <a name="test-cases"></a>Casos de teste
 A seguir, casos específicos de teste para a área de teste Adicionar/Abrir do Controle de Origem.

### <a name="case-1a-add-solution-to-source-control"></a>Caso 1a: Adicionar solução ao controle de origem
 Este caso de teste se concentra em adicionar soluções ao controle de origem.

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Adicionar solução contendo um projeto cliente ao controle de origem|1. Crie um projeto cliente.<br />2. Adicione a solução ao controle de origem **(Arquivo,** **Controle de Origem,** **Adicionar Solução ao Controle de Origem**).|Solução/Projeto foi adicionado ao controle de origem.|
|Adicionar solução contendo um sistema de arquivos ou projeto Web IIS local para controle de origem|1. Crie um sistema de arquivos ou um projeto Web IIS local (use o botão Procurar para apontar a localização do projeto; o caminho determina que tipo de projeto web é criado).<br />2. Adicione a solução ao controle de origem **(Arquivo,** **Controle de Origem,** **Adicionar Solução ao Controle de Origem**).|Solução/Projeto foi adicionado ao controle de origem.|
|Adicionar solução contendo um projeto web do site remoto para controle de origem|1. Crie um projeto web de site remoto.<br />2. Adicione a solução ao controle de origem **(Arquivo,** **Controle de Origem,** **Adicionar Solução ao Controle de Origem**).<br />3. Clique em **OK** na caixa de diálogo de aviso do FrontPage Access.|A solução foi adicionada ao controle de origem.<br /><br /> O projeto do Site Remoto NÃO está sob controle de origem. (Os projetos de sites remotos devem ser controlados a partir de seu próprio servidor IIS.)|
|Adicione uma única solução de projeto ao controle de origem usando **adicionar projetos selecionados ao controle de origem**.|1. Crie uma única solução de projeto.<br />2. Adicione apenas a solução ao controle de origem como uma seleção **(Arquivo,** **Controle de Origem,** **Adicionar Projetos Selecionados ao Controle de Origem**). Se esse passo for bem sucedido, continue até o próximo passo.<br />3. Adicionar projeto ao controle de origem como seleção **(Arquivo,** **Controle de Origem,** **Adicionar Projetos Selecionados ao Controle de Origem**).<br />4. Clique **em Sim** para adicionar o projeto ao mesmo local.<br />5. Clique em **Sair** para editar a caixa de diálogo **Para editar.**|`Result from Step 2:`<br /><br /> O projeto e todos os arquivos dentro do projeto têm um indicador de controle de origem verificado, e uma Dica de Ferramenta exibe "Não sob controle de origem".<br /><br /> `Result from Step 5:`<br /><br /> O arquivo de projeto e solução estão na mesma pasta no controle de origem.|
|Cancele a adição de uma solução para o controle de origem|1. Crie uma única solução de projeto.<br />2. Tente adicionar projeto e solução ao controle de origem. Se esse passo for bem sucedido, continue até o próximo passo.<br />3. Cancele depois de entrar no sistema de controle de origem.|`Result from Step 2:`<br /><br /> A caixa de diálogo de controle de origem de localização do projeto Set é exibida apenas uma vez.<br /><br /> `Result from Step 3:`<br /><br /> O projeto adicionar cancelado, projeto/solução NÃO está sob controle de origem e todos adicionar aos menus de controle de origem ainda disponíveis.|

### <a name="case-1b-open-solution-from-source-control"></a>Caso 1b. Solução aberta do controle de origem
 Este caso de teste se concentra na abertura de soluções do controle de origem.

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Abra uma solução contendo um projeto de cliente a partir do controle de origem|1. Crie um projeto cliente.<br />2. Adicione a solução ao controle de origem.<br />3. Feche a solução.<br />4. Abra a solução do controle de origem para um novo local.|Solução/Projeto aberto a partir do controle de origem.|
|Abra uma solução contendo um projeto Web local ou IIS a partir do controle de origem|1. Crie um projeto web local ou IIS.<br />2. Adicione a solução ao controle de origem.<br />3. Feche a solução.<br />4. Abra a solução do controle de origem para um novo local.|Solução/Projeto aberto a partir do controle de origem.|
|Abra uma solução contendo um projeto web do site remoto a partir do controle de origem|1. Crie um projeto web de site remoto.<br />2. Adicione a solução ao controle de origem. Se esse passo for bem sucedido, continue até o próximo passo.<br />3. Feche a solução.<br />4. Abra a solução do controle de origem para um novo local.|`Result from Step 2:`<br /><br /> O Site Remoto da Web NÃO está sob controle de origem.<br /><br /> `Result from Step 4:`<br /><br /> Solução aberta a partir do controle de origem.<br /><br /> O projeto Do Local Remoto está carregado, mas NÃO está sob controle de origem.|

### <a name="case-1c-add-solution-from-source-control"></a>Caso 1c: Adicionar solução do controle de origem
 Este caso de teste se concentra em adicionar soluções do controle de origem.

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Adicionar à solução Empty — uma única solução de projeto|1. Crie uma única solução de projeto.<br />2. Adicione a solução ao controle de origem.<br />3. Feche a solução.<br />4. Crie uma segunda solução vazia.<br />5. Adicione a solução previamente controlada a partir do controle de origem **(Arquivo,** **Controle de Origem,** **Adicionar Projeto do Controle de Origem**).|O projeto adicionado aparece no **Solution Explorer** e é verificado.|
|Adicionar à solução com um único projeto — projeto único|1. Crie uma solução com um único projeto.<br />2. Adicione a solução ao controle de origem.<br />3. Feche a solução.<br />4. Crie uma segunda solução vazia.<br />5. Adicione a solução previamente controlada a partir do controle de origem **(Arquivo,** **Controle de Origem,** **Adicionar Projeto do Controle de Origem**).|O projeto adicionado aparece no **Solution Explorer** e é verificado.|
|Adicionar à solução — solução adicionada ao controle de origem por seleção|1. Crie uma solução com um projeto.<br />2. Adicione apenas a solução ao controle de origem como seleção. Se esse passo for bem sucedido, continue até o próximo passo.<br />3. Feche a solução.<br />4. Crie uma nova solução.<br />5. Adicione a solução previamente controlada a partir do controle de origem **(Arquivo,** **Controle de Origem,** **Adicionar Projeto do Controle de Origem**).|`Result from Step 2:`<br /><br /> O projeto não está sob controle de origem.<br /><br /> `Result from Step 5:`<br /><br /> Se a primeira solução tivesse itens de solução, eles não podem ser adicionados do controle de origem, de modo que eles não aparecem.<br /><br /> O projeto da primeira solução aparece como indisponível.|

## <a name="see-also"></a>Confira também
- [Guia de teste para plug-ins de controle do código-fonte](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
