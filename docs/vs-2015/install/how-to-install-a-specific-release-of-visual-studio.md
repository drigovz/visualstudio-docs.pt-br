---
title: Como instalar um lançamento específico | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- install a specific release, Visual Studio
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: dde0cefabf0523484ad76ac56f7f2760de8c7acc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838552"
---
# <a name="how-to-install-a-specific-release-of-visual-studio"></a>Como: instalar uma versão específica do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Atualizamos a instalação do Visual Studio com frequência para que você obtenha a versão mais recente e otimizada dos nossos recursos opcionais.  Mas se quiser instalar um lançamento anterior do Visual Studio 2015, por exemplo, um lançamento da pré-atualização 1 do Visual Studio com suporte para iOS, será necessário forçar uma atualização do programa para usar uma versão anterior dos respectivos arquivos de manifesto do recurso. Este artigo descreve como fazê-lo.

## <a name="installing-the-current-release"></a>Como instalar o lançamento atual
 Atualizamos diversas vezes o mecanismo de instalação e os arquivos de manifesto, desde o lançamento inicial do Visual Studio 2015.  Isso significa que, se baixar o instalador da Web do site de [Downloads do Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs) em um computador limpo conectado à Internet, você instalará a atualização mais recente do Visual Studio 2015, que inclui os aprimoramentos mais recentes do produto, bem como as versões mais novas de ferramentas e recursos adicionais.

## <a name="installing-earlier-releases"></a>Como instalar lançamentos anteriores
 É possível criar e montar uma imagem ISO ou baixar e iniciar o instalador diretamente da página [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015), e inserir o arquivo .exe com parâmetros de linha de comando adicionais, como /CustomInstallPath, /Full, /InstallSelectableItems, /NoRestart, etc., para controlar o modo de instalação do Visual Studio.

 A tabela a seguir inclui alguns cenários pontuais específicos e os parâmetros de linha de comando necessários que devem ser passados para o instalador do Enterprise Edition. Os mesmos parâmetros funcionarão também com os instaladores do Professional Edition e do Community Edition.

|Edição do Visual Studio 2015|O que executar|Linha de comando a usar|O que a instalação faz|
|--------------------------------|-----------------|--------------------------|---------------------|
|Visual Studio Enterprise (o lançamento público mais recente)|Visual Studio Enterprise com atualizações (disponível em [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015))|`vs_enterprise.exe` **Observação:** o comportamento padrão dessa instalação oferece os recursos opcionais mais recentes, portanto, ela não exige parâmetros de linha de comando.|A instalação do Visual Studio usará o arquivo feed.xml mais recente e instalará os arquivos mais recentes|
|Visual Studio Enterprise com a Atualização 3 (a Atualização 3 original, sem outras atualizações lançadas na mesma época)|Visual Studio Enterprise RTM (disponível na [página de download de assinaturas do MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|A instalação do Visual Studio usará o arquivo feed.xml disponibilizado no lançamento da Atualização 3|
|Visual Studio Enterprise com a Atualização 2 (a Atualização 2 original, mas com atualizações que precederam a Atualização 3)|Visual Studio Enterprise RTM (disponível na [página de download de assinaturas do MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|A instalação do Visual Studio usará o arquivo feed.xml disponibilizado antes do lançamento da Atualização 3|
|Visual Studio Enterprise (a Atualização 2 original, sem outras atualizações lançadas na mesma época)|Visual Studio Enterprise RTM (disponível na [página de download de assinaturas do MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|A instalação do Visual Studio usará o arquivo feed.xml disponibilizado no lançamento da Atualização 2|
|Visual Studio Enterprise com a Atualização 1 (a Atualização 1 original, mas com atualizações que precederam a Atualização 2)|Visual Studio Enterprise RTM (disponível na [página de download de assinaturas do MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|A instalação do Visual Studio usará o arquivo feed.xml disponibilizado antes do lançamento da Atualização 2|
|Visual Studio Enterprise com a Atualização 1 (a Atualização 1 original, sem outras atualizações lançadas na mesma época)|Visual Studio Enterprise RTM (disponível na [página de download de assinaturas do MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|A instalação do Visual Studio usará o arquivo feed.xml disponibilizado no lançamento da Atualização 1|
|Visual Studio Enterprise (o RTM original, mas com atualizações que precederam a Atualização 1)|Visual Studio Enterprise RTM (disponível na [página de downloads de Assinaturas do MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|A instalação do Visual Studio usará o arquivo feed.xml disponibilizado antes do lançamento da Atualização 1|
|Visual Studio Enterprise (o RTM original sem atualizações)|Visual Studio Enterprise RTM (disponível na [página de download de assinaturas do MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|A instalação do Visual Studio usará o arquivo feed.xml disponibilizado no lançamento do RTM|

> [!IMPORTANT]
> Dependendo do idioma que você deseja usar, substitua "enu" (para inglês) por um dos seguintes valores:
>
> - chs (para chinês (simplificado))
>   - cht (para chinês (tradicional))
>   - csy (para tcheco)
>   - deu (para alemão)
>   - esn (para espanhol)
>   - fra (para francês)
>   - ita (para italiano)
>   - jpa (para japonês)
>   - kor (para coreano)
>   - plk (para polonês)
>   - ptb (para português)
>   - rus (para russo)
>   - trk (para turco)

## <a name="see-also"></a>Consulte Também
 [Guia do administrador do Visual Studio](../install/visual-studio-administrator-guide.md)