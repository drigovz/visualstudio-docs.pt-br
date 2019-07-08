---
title: Controle de Versão do Team Foundation (TFVC)
description: Conexão do Visual Studio para Mac ao Team Foundation Server/Azure DevOps com o Controle de Versão do Team Foundation (TFVC).
author: conceptdev
ms.author: crdun
ms.date: 06/25/2019
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 04a251621af1086c15bafa15b7a9fe01f8dab5a8
ms.sourcegitcommit: 9d3529e40438ca45dcb0b31742c4cd5a89daa61e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398977"
---
# <a name="connecting-to-team-foundation-version-control"></a>Conexão com o Controle de Versão do Team Foundation

> [!NOTE]
> Para obter a melhor experiência de controle de versão no macOS, recomendamos o uso do Git em vez do Controle de Versão do Team Foundation (TFVC). O Git é suportado no Visual Studio para Mac e é a opção padrão para repositórios hospedados no Team Foundation Server (TFS)/Azure DevOps. Para saber mais sobre como usar o Git com o TFS/Azure DevOps, confira o artigo [Configurar um Repositório Git](/visualstudio/mac/set-up-git-repository).
> 
> Se a versão prévia da extensão do TFVC para o Visual Studio para Mac foi usada anteriormente, ela não é mais compatível no Visual Studio 2019 para Mac.

O Azure Repos fornece dois modelos de controle de versão: [Git](/azure/devops/repos/git/?view=azure-devops), um sistema de controle de versão distribuído, e [Controle de Versão do Team Foundation](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC), um sistema de controle de versão centralizado.

O Visual Studio para Mac fornece suporte completo para repositórios Git, mas requer algumas soluções alternativas para trabalhar com o TFVC. Se você estiver usando o TFVC para o controle de versão hoje, veja abaixo algumas soluções que você poderá usar para acessar seu código-fonte hospedado no TFVC:

* [Usar o Visual Studio Code e a extensão Azure Repos para uma interface gráfica](#use-visual-studio-code-and-the-azure-repos-extension)
* [Conectar-se ao seu repositório usando o cliente de linha de comando Team Explorer Everywhere (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)

O restante deste artigo explica as opções listadas acima.

## <a name="requirements"></a>Requisitos

* Visual Studio Community, Professional ou Enterprise para Mac versão 7.8 e posterior.
* Azure DevOps Services, Team Foundation Server 2013 e posterior, ou Azure DevOps Server 2018 e posterior.
* Um projeto no Azure DevOps Services ou no Team Foundation Server/Azure DevOps Server, configurado para usar o Controle de Versão do Team Foundation.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Usar o Visual Studio Code e a extensão Azure Repos

Se você gosta de trabalhar com uma interface gráfica para gerenciar seus arquivos no controle de versão, a extensão Azure Repos para o Visual Studio Code fornece uma solução com suporte da Microsoft. Para começar, faça o download do [Visual Studio Code](https://code.visualstudio.com) e saiba como [configurar a extensão do Azure Repos](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Conectar-se usando o cliente de linha de comando Team Explorer Everywhere

Se você se sentir confortável usando o macOS Terminal, o Cliente de Linha de Comando do Team Explorer Everywhere (TEE-CLC) fornecerá uma forma com suporte de se conectar à sua fonte no TFVC.

Você pode seguir as etapas abaixo para configurar sua conexão com o TFVC e confirmar as alterações.

### <a name="setting-up-the-tee-clc"></a>Configurar o TEE-CLC

Há duas maneiras de configurar com o TEE-CLC.

* Use o Homebrew para instalar o cliente ou
* Baixe e instale manualmente o cliente

A solução mais fácil é **usando o HomeBrew**, que é um gerenciador de pacotes para macOS. Para instalar usando esse método:

1. Inicie o aplicativo macOS Terminal.
1. Instale o Homebrew usando o Terminal e as instruções na [página inicial do Homebrew](https://brew.sh/).
1. Uma vez instalado o Homebrew, execute o seguinte comando no seu Terminal: `brew install tee-clc`

Para **configurar manualmente o TEE-CLC**:

1. [Faça o download da versão mais recente do tee-clc](https://github.com/Microsoft/team-explorer-everywhere/releases) da página de lançamentos do repositório GitHub Team Explorer Everywhere (por exemplo, tee-clc-14.134.0.zip no momento desta publicação).
1. Extraia o conteúdo do .zip para uma pasta no disco.
1. Abra o aplicativo macOS Terminal e use o comando `cd` para alternar para a pasta usada na etapa anterior.
1. Na pasta, execute o comando `./tf` para testar se o cliente da linha de comando pode ser executado, você pode ser solicitado a instalar o Java ou outras dependências.

Depois que o TEE-CLC estiver instalado, você poderá executar o comando `tf eula` para visualizar e aceitar o contrato de licença do cliente.

Por fim, para autenticar com seu ambiente TFS/Azure DevOps, você precisará criar um token de acesso pessoal no servidor. Saiba mais sobre [autenticação com tokens de acesso pessoal](https://docs.microsoft.com/azure/devops/integrate/get-started/authentication/pats?view=azure-devops). Ao criar um token de acesso pessoal para usar com o TFVC, certifique-se de fornecer acesso completo ao configurar o token.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Usar o TEE-CLC para se conectar ao seu repositório

Para se conectar ao seu código-fonte, primeiro você precisa criar um espaço de trabalho usando o comando `tf workspace`. Por exemplo, os seguintes comandos se conectam a uma Organização no Azure DevOps Services chamada "MyOrganization": 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

A configuração do ambiente `TF_AUTO_SAVE_CREDENTIALS` é usada para salvar suas credenciais, para que você não seja solicitado a inseri-las várias vezes. Quando for solicitado um nome de usuário, use o token de acesso pessoal criado na seção anterior e use uma senha em branco.

Para criar um mapeamento de seus arquivos de origem para uma pasta local, você usará o comando `tf workfold`. O exemplo a seguir mapeará uma pasta chamada "WebApp.Services" do projeto TFVC "MyRepository" e a configurará para ser copiada para a pasta ~/Projects/ local (ou seja, uma pasta "Projects" na pasta inicial dos usuários atuais).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Por fim, use o seguinte comando para obter os arquivos de origem do servidor e copiá-los localmente:

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>Confirmar as alterações usando o TEE-CLC

Depois de fazer alterações em seus arquivos no Visual Studio para Mac, você pode voltar ao Terminal para verificar suas edições. O comando `tf add` é usado para adicionar arquivos à lista de alterações pendentes a serem registradas e o comando `tf checkin` executa a entrada real no servidor. O comando `checkin` inclui parâmetros para adicionar um comentário ou associar um item de trabalho relacionado. No trecho de código a seguir, todos os arquivos em uma pasta `WebApp.Services` são adicionados, recursivamente, ao check-in. Em seguida, o código é verificado com um comentário e associado a um item de trabalho com a ID "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Para aprender mais sobre os comandos mencionados aqui, ou outros, você pode usar o seguinte comando do Terminal:

`tf help`

### <a name="see-also"></a>Consulte também

- [Develop and share your code in TFVC using Visual Studio (on Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs) [Desenvolver e compartilhar seu código no TFVC usando o Visual Studio (no Windows)]