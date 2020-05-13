---
title: 'Área de teste 2: obter do controle de origem | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c213e2774730596db8b8e4f2d0691472495222e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704597"
---
# <a name="test-area-2-get-from-source-control"></a>Área de teste 2: obter do controle do código-fonte
Esta área de teste cobre casos de teste para recuperar itens da loja de versões através do comando Get. Esses casos de teste podem ser aplicados tanto em projetos locais quanto em projetos web.

## <a name="command-menu-access"></a>Acesso ao menu de comando
 Os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seguintes caminhos do menu do ambiente de desenvolvimento integrado são usados nos casos de teste.

##### <a name="get-latest-version"></a>Obter versão mais recente:

- **Arquivo,** **controle de origem,** **obter versão mais recente**.

- **Arquivo**, **obter versão mais recente**.

- Menu de atalho, **obter versão mais recente**.

- Obter: **Arquivo,** **Controle de Origem,** **Obter**.

## <a name="expected-behavior"></a>Comportamento esperado

##### <a name="get-latest-version"></a>Obter versão mais recente:
 Realiza uma recuperação silenciosa (sem ui) da versão mais recente do item da loja de versões.

##### <a name="get"></a>Obter:
 Exibe a caixa de diálogo **Obter** e permite que o usuário faça alterações no conjunto de arquivos que serão recuperados, bem como modifique as opções que afetam a forma como os arquivos são recuperados.

## <a name="test-cases"></a>Casos de teste

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Obtenha a versão mais recente de um arquivo que NÃO existe localmente|1. Crie um projeto.<br />2. Adicione um item ao projeto.<br />3. Coloque o projeto sob controle de origem.<br />4. Exclua a cópia local do item.<br />5. Obtenha a versão mais recente do item (Menu de atalho, **obtenha a versão mais recente**).|O arquivo do item é recuperado localmente.|
|Obtenha um arquivo que NÃO existe localmente|1. Crie um projeto.<br />2. Adicione um item ao projeto.<br />3. Coloque o projeto sob controle de origem.<br />4. Exclua a cópia local do item.<br />5. Obtenha o item **(Arquivo,** **Controle de Origem,** **Obtenha** \<o item>).|O arquivo do item é recuperado localmente.|
|Obtenha um arquivo que foi verificado exclusivamente e modificado localmente|1. Crie um projeto.<br />2. Adicione um item ao projeto.<br />3. Coloque o projeto sob controle de origem.<br />4. Confira o item do projeto com exclusividade.<br />5. Modifique a cópia local.<br />6. Obtenha a versão mais recente do item **(Arquivo,** **Obtenha a versão mais recente do** \<item>). Se esse passo for bem sucedido, continue até o próximo passo.<br />7. Clique em **Substituir** o botão na caixa de diálogo de aviso.|**Reresultado da Etapa 6**`:`<br /><br /> A caixa de diálogo de aviso indica que o arquivo foi verificado.<br /><br /> **Reresultado do passo 7:**<br /><br /> O arquivo local modificado é substituído pela versão original da loja de versões.<br /><br /> O arquivo é lido/escrito.|
|Obter e Substituir o arquivo que é verificado, compartilhado e modificado localmente|1. Crie um novo projeto.<br />2. Adicione um item ao projeto.<br />3. Coloque o projeto sob controle de origem.<br />4. Confira o item do projeto como compartilhado.<br />5. Modifique a cópia local.<br />6. Obtenha a versão mais recente do item **(Arquivo,** **Obtenha a versão mais recente do** \<item>). Se esse passo for bem sucedido, continue até o próximo passo.<br />7. Clique em **Substituir** na caixa de diálogo de aviso.|**Resultado do Passo 6:**<br /><br /> A caixa de diálogo de aviso indica que o arquivo foi verificado.<br /><br /> **Resultado do Passo 7:**<br /><br /> O arquivo local modificado é substituído pela versão original da loja de versões.<br /><br /> O arquivo é lido/escrito.|
|Obtenha um arquivo que EXISTE localmente, o mesmo que a versão mais recente na loja de versões|1. Crie um novo projeto.<br />2. Adicione um item ao projeto.<br />3. Coloque o projeto sob controle de origem.<br />4. Obtenha o item **(Arquivo,** **Controle de Origem,** **Obter** \<item>).|O arquivo local está inalterado.|
|Obtenha uma solução com um projeto|1. Crie uma solução com um projeto.<br />2. Coloque a solução sob controle de origem.<br />3. Exclua todos os arquivos do projeto localmente.<br />4. Obtenha a solução **(Arquivo,** **Controle de Origem,** **Obter**).|Todos os arquivos excluídos são restaurados localmente.|

## <a name="see-also"></a>Confira também
- [Guia de teste para plug-ins de controle do código-fonte](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
