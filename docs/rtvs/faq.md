---
title: Perguntas Frequentes sobre as Ferramentas do R para Visual Studio
description: Perguntas frequentes sobre R no Visual Studio.
ms.date: 12/04/2017
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 4eef8e79023bdd3bde03fec33c16a1c8f6d90446
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72306267"
---
# <a name="frequently-asked-questions"></a>Perguntas frequentes

## <a name="visual-studio-support"></a>Suporte do Visual Studio

**P. O RTVS funciona no OS X ou Linux?**

a. Atualmente, as RTVS se baseiam no Visual Studio, que é uma implementação somente do Windows. A Microsoft está analisando o suporte no Visual Studio Code e no Visual Studio para Mac. Consulte a [edição nº 1295 do RTVS](https://github.com/Microsoft/RTVS/issues/1295).

**P. O RTVS funciona com edições do Visual Studio Express?**

a. Não.

**P. Posso usar extensões do Visual Studio com RTVS?**

a. Com certeza. Na verdade, aqui estão algumas opções que são comuns para pessoas que trabalham com o R.

- [VsVim para associações de chave vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Editor de markdown com visualização em tempo real](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Veja o [Visual Studio Marketplace](https://marketplace.visualstudio.com/) para saber mais.

**P. Como o RTVS está no Visual Studio, isso significa que R pode ser facilmente usado com C#, C++ e outros idiomas da Microsoft?**

a. Não. As RTVS são uma ferramenta para desenvolver código R e usa os intérpretes nativos de R padrão. Atualmente, não há suporte para interoperabilidade entre o R e outras linguagens.

**P. O RTVS funciona com um local não inglês?**

a. A versão 1.0 do RTVS será somente em inglês. A versão 1.1 será localizado para o mesmo conjunto de idiomas do Visual Studio. Enquanto isso, use o [Pacote do idioma inglês para o Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48157) ou, no Visual Studio 2017, execute o instalador e selecione inglês na guia **Pacotes de idiomas**.

![Configurações internacionais do Visual Studio 2017](media/FAQ-international-settings.png)

**P. Eu realmente gosto das minhas configurações atuais do Visual Studio, mas eu quero experimentar as novas configurações de Ciência de Dados. O que eu devo fazer?**

a. Salve as configurações atuais do Visual Studio usando **configurações** > **de importação e exportação de ferramentas**e mude para as configurações de Ciência de Dados. Para restaurar as configurações salvas, use o comando **Importar e Exportar Configurações** novamente.

**P. Posso armazenar meu projeto do Visual Studio em um compartilhamento de rede?**

a. Não, o Visual Studio não dá suporte ao carregamento de projetos de um compartilhamento de rede.

## <a name="r-interpretersintegration"></a>Interpretadores/integração do R

**P. Com que intérpretes R trabalha rtvs?**

a. [CRAN R](https://cran.r-project.org/), [Microsoft R Client e Microsoft Machine Learning Server](/machine-learning-server/)

**P. Onde posso baixar esses intérpretes?**

a. Veja [Instalação](installing-r-tools-for-visual-studio.md).

P. **O que é o Microsoft R Server?**

a. R Server é o antigo nome do [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**P. O RTVS funciona com edições de 32 bits de R?**

a. Não, as RTVS só dão suporte às edições de 64 bits do R em execução em edições de 64 bits do Windows.

**P. O RTVS funciona com o meu sistema de controle de origem?**

a. Sim, você pode usar qualquer sistema de controle do código-fonte que esteja integrado ao Visual Studio.

**P. Quais são as configurações *.gitignore* recomendadas para um projeto RTVS?**

a. O GitHub mantém um repositório mestre de arquivos *.gitignore* recomendados. Você pode vê-lo aqui: [.gitignore do R](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Serviços remotos

Q. **O que são os Serviços Remotos no Visual Studio?**

a. Os Serviços Remotos do R para Visual Studio permitem configurar um computador Windows ou Linux e, em seguida, conectar-se a ele por meio do RTVS. Veja [Configurar workspaces remotos](setting-up-remote-r-workspaces.md).

Q. **As RTVS podem se conectar ao Microsoft Machine Learning Server?**

a. Não, porque o Microsoft ML Server é uma tecnologia diferente e não fornece o mesmo mecanismo de conectividade que as RTVS exigem.

Q. **O RTVS pode se conectar a uma VM criada usando a imagem de VM de ciência de dados no Azure?**

a. Sim, a imagem [VM de ciência de dados – Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) vem pré-instalada com os Serviços R Remotos para Visual Studio.

P. **O RTVS pode se conectar a um computador remoto com R instalado?**

Para executar código R em um computador remoto, deve haver algum serviço de escuta para as solicitações, recebendo o código e enviando os resultados de volta para o computador cliente. É isto que os Serviços Remotos do R para Visual Studio fazem. Veja [Configurar workspaces remotos](setting-up-remote-r-workspaces.md).

Q. **O que é a sessão remota?**

a. Consulte o artigo [Executar no servidor remoto](/machine-learning-server/r/how-to-execute-code-remotely) na documentação do Machine Learning Server.

## <a name="rtvs-development-and-features"></a>Recursos e desenvolvimento do RTVS

**Q. Recurso X está faltando, mas RStudio tem!**

a. O RStudio é um IDE fantástico e maduro para R que vem sendo desenvolvido há vários anos. As RTVS procuram ter todos os recursos mais importantes que você precisa para ser bem-sucedido. Ajude a priorizar o trabalho futuro, arquivando problemas no [GitHub](https://github.com/Microsoft/RTVS/issues/).

**P. Posso contribuir para o RTVS?**

a. Claro que não! O código-fonte reside no [Github](https://github.com/microsoft/RTVS). Use o rastreador de problemas para enviar bugs e comentar sobre aqueles já arquivados.

Você também pode contribuir com esta documentação &mdash; basta selecionar o comando **Editar** no canto superior direito de qualquer página. Os comentários sobre os documentos também são bem-vindos, os quais você pode adicionar à parte inferior de qualquer página.
