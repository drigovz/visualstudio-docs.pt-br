---
title: 'Solução de problemas: Como fazer liberar uma nova versão da minha extensão existente?'
description: Um guia sobre como atualizar extensões existentes por meio do fluxo de trabalho de publicação.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/14/2020
ms.technology: vs-ide-general
ms.assetid: 5DA76197-7859-421f-AC45-401F22F5D794
ms.topic: troubleshooting
ms.openlocfilehash: 862ae404571da44d9ca28db2c94d2ebeb39ce79f
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488458"
---
# <a name="troubleshooting-how-do-i-release-a-new-version-of-my-existing-extension"></a>Solução de problemas: Como fazer liberar uma nova versão da minha extensão existente?

> [!IMPORTANT]
> Atualmente, a criação de novas extensões não é oficialmente suportada no Visual Studio 2019 para Mac.

O servidor de repositório de extensão de Visual Studio para Mac será movido em 15 de janeiro de 2021. Essa movimentação não afetará os usuários que já baixaram sua extensão, mas mudará a maneira como você publica novas versões da extensão após essa data.

Como autor de uma extensão existente, você precisará seguir um fluxo de trabalho diferente para liberar mais atualizações. Esse processo consiste em:
- Configurando um repositório GitHub público para cada extensão
- Compartilhando a URL do repositório para a equipe de Visual Studio para Mac por meio da [lista de endereçamento de publicação de extensão](mailto:vsmextpub@microsoft.com)
- Atualizando sua extensão usando o recurso de versões no GitHub


## <a name="initial-setup"></a>Instalação inicial 

Para continuar publicando atualizações em suas extensões, você precisará criar um repositório GitHub público. Se você publicar várias extensões, precisará ter um repositório separado para cada um, a menos que você sempre tenha a versão e publique-os juntos, caso em que você pode usar um único repositório.

> [!NOTE]
> Embora o repositório GitHub para sua extensão precise ser público, você não precisa hospedar nenhum do seu código. Seguir esse processo não exige que você tenha qualquer um de seus códigos no GitHub.


## <a name="share-the-location-of-your-repository"></a>Compartilhar o local do seu repositório

Depois de configurar o repositório, envie um email para a lista de [endereçamento de publicação de extensão](mailto:vsmextpub@microsoft.com) com a URL.


## <a name="release-a-new-version"></a>Liberar uma nova versão

Você usará o link "criar uma nova versão" na página principal do repositório para iniciar o processo de atualização de sua extensão. Depois de selecionar esse link, siga estas etapas:

1. Adicione informações à **versão de marca** da versão no seguinte formato

    > \<releaseVersion> \- VSM v\<targetVersion>

    Em que:
     - **&lt; releaseVersion &gt;** é o número de versão da extensão
     - **&lt; targetVersion &gt;** é a versão mínima do Visual Studio para Mac sua extensão está direcionando

2. Adicional Os campos **título** e **Descrição** podem ser preenchidos com as informações desejadas; Esse fluxo de trabalho não usa as informações contidas nesses campos.

3. Verifique se a caixa de seleção **pré-lançamento** está desmarcada. Se estiver marcada, a versão não será selecionada por esse processo de publicação.

4. Anexe os arquivos **. mPack** que implementam sua extensão na seção de **binários** . É possível anexar vários arquivos **. mPack** em uma versão.

Visual Studio para Mac exibirá a versão mais recente da extensão que é compatível com a Visual Studio para Mac instalação que foi usada para acessar o repositório de extensões.

Desde que você tenha registrado seu repositório GitHub com a equipe de Visual Studio para Mac, sua versão de extensão será coletada por Visual Studio para Mac dentro de 24 horas.

## <a name="additional-information"></a>Informações adicionais

- As versões que não estão em conformidade com os requisitos detalhados acima não serão publicadas. 
- Após 15 de janeiro de 2021, as atualizações de extensão só aparecerão no Visual Studio para Mac 8,0 ou mais recente.
- As extensões existentes permanecerão disponíveis para Visual Studio para Mac usuários sem nenhuma ação de sua parte. Você só precisa seguir as instruções neste guia se publicar uma nova versão após 15 de janeiro de 2021.
