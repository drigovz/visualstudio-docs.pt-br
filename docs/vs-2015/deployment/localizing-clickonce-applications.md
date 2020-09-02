---
title: Localizando aplicativos ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, ClickOnce applications
- ClickOnce deployment, globalization
- deploying applications [ClickOnce], localizing ClickOnce applications
- localization, ClickOnce deployment
- ClickOnce deployment, download on-demand
- ClickOnce deployment, localization
- Windows Forms, ClickOnce applications
- console applications, ClickOnce applications
ms.assetid: c92b193b-054d-4923-834b-d4226a4c7a1a
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3c29bd6a58d510d98f2a08c96d0cd0bc774e197e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679990"
---
# <a name="localizing-clickonce-applications"></a>Localização de aplicativos ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A localização é o processo de tornar seu aplicativo apropriado para uma cultura específica. Esse processo envolve a conversão de texto da interface do usuário em uma linguagem específica da região, usando a formatação correta de data e moeda, ajustando o tamanho dos controles em um formulário e espelhando controles da direita para a esquerda, se necessário.  
  
 Localizar o aplicativo resulta na criação de um ou mais assemblies satélite. Cada assembly contém cadeias de caracteres de interface do usuário, imagens e outros recursos específicos de uma determinada cultura. (O arquivo executável principal do seu aplicativo contém as cadeias de caracteres para a cultura padrão para seu aplicativo.)  
  
 Este tópico descreve três maneiras de implantar um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo para outras culturas:  
  
- Inclua todos os assemblies satélite em uma única implantação.  
  
- Gere uma implantação para cada cultura, com um único assembly satélite incluído em cada um.  
  
- Baixar assemblies satélites sob demanda.  
  
## <a name="including-all-satellite-assemblies-in-a-deployment"></a>Incluindo todos os assemblies satélite em uma implantação  
 Em vez de publicar várias [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantações, você pode publicar uma única [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação que contenha todos os assemblies satélite.  
  
 Esse método é o padrão no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Para usar esse método no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , você não precisa fazer nenhum trabalho adicional.  
  
 Para usar esse método com MageUI.exe, você deve definir a cultura do seu aplicativo como **neutra** em MageUI.exe. Em seguida, você deve incluir manualmente todos os assemblies satélite em sua implantação. No MageUI.exe, você pode adicionar os assemblies satélite usando o botão **popular** na guia **arquivos** do manifesto do aplicativo.  
  
 A vantagem dessa abordagem é que ela cria uma única implantação e simplifica sua história de implantação localizada. Em tempo de execução, o assembly satélite apropriado será usado, dependendo da cultura padrão do sistema operacional Windows do usuário. Uma desvantagem dessa abordagem é que ela baixa todos os assemblies satélite sempre que o aplicativo é instalado ou atualizado em um computador cliente. Se seu aplicativo tiver um grande número de cadeias de caracteres ou se seus clientes tiverem uma conexão de rede lenta, esse processo poderá afetar o desempenho durante a atualização do aplicativo.  
  
> [!NOTE]
> Essa abordagem pressupõe que seu aplicativo ajuste a altura, a largura e a posição de controles automaticamente para acomodar tamanhos de cadeia de caracteres de texto diferentes em diferentes culturas. O Windows Forms contém uma variedade de controles e tecnologias que permitem que você projete seu formulário para torná-lo facilmente localizável, incluindo os <xref:System.Windows.Forms.FlowLayoutPanel> controles e, <xref:System.Windows.Forms.TableLayoutPanel> bem como a <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade.  Consulte também [como oferecer suporte à localização em Windows Forms usando AutoSize e o controle TableLayoutPanel](https://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\)).  
  
## <a name="generate-one-deployment-for-each-culture"></a>Gerar uma implantação para cada cultura  
 Nessa estratégia de implantação, você gera várias implantações. Em cada implantação, você inclui apenas o assembly satélite necessário para uma cultura específica e marca a implantação como específica para essa cultura.  
  
 Para usar esse método no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , defina a propriedade **idioma de publicação** na guia **publicar** para a região desejada. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o incluirá automaticamente o assembly satélite necessário para a região selecionada e excluirá todos os outros assemblies satélites da implantação.  
  
 Você pode fazer a mesma coisa usando a ferramenta de MageUI.exe na Microsoft [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . Use o botão **popular** na guia **arquivos** do manifesto do aplicativo para excluir todos os outros assemblies satélite do diretório do aplicativo e, em seguida, defina o campo **cultura** na guia **nome** do manifesto de implantação no MageUI.exe. Essas etapas não apenas incluem o assembly satélite correto, mas também definem o `language` atributo no `assemblyIdentity` elemento em seu manifesto de implantação para a cultura correspondente.  
  
 Depois de publicar o aplicativo, você deve repetir essa etapa para cada cultura adicional à qual seu aplicativo dá suporte. Você deve certificar-se de publicar em um diretório de servidor Web ou diretório de compartilhamento de arquivos diferente sempre, porque cada manifesto do aplicativo fará referência a um assembly satélite diferente e cada manifesto de implantação terá um valor diferente para o `language` atributo.  
  
## <a name="downloading-satellite-assemblies-on-demand"></a>Baixando assemblies satélite sob demanda  
 Se você decidir incluir todos os assemblies satélite em uma única implantação, poderá melhorar o desempenho usando o download sob demanda, o que permite marcar assemblies como opcionais. Os assemblies marcados não serão baixados quando o aplicativo for instalado ou atualizado. Você pode instalar os assemblies quando precisar deles chamando o <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> método na <xref:System.Deployment.Application.ApplicationDeployment> classe.  
  
 O download de assemblies satélite sob demanda difere ligeiramente de baixar outros tipos de assemblies sob demanda. Para obter mais informações e exemplos de código sobre como habilitar esse cenário usando o [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] ferramentas para o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], consulte [passo a passo: baixando Assemblies de satélite por demanda com a API de implantação do ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md).  
  
 Você também pode habilitar esse cenário no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  Consulte também [instruções passo a passo: baixando Assemblies de satélite sob demanda com o ClickOnce Deployment API usando o Designer](https://msdn.microsoft.com/library/ms366788\(v=vs.110\)) ou [passo a passo: baixando Assemblies de satélite por demanda com a API de implantação do ClickOnce Usando o Designer](https://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
## <a name="testing-localized-clickonce-applications-before-deployment"></a>Testando aplicativos ClickOnce localizados antes da implantação  
 Um assembly satélite será usado para um aplicativo Windows Forms somente se a <xref:System.Threading.Thread.CurrentUICulture%2A> Propriedade do thread principal do aplicativo for definida como a cultura do assembly satélite. Os clientes em mercados locais provavelmente já estarão executando uma versão localizada do Windows com a cultura definida para o padrão apropriado.  
  
 Você tem três opções para testar implantações localizadas antes de tornar seu aplicativo disponível para os clientes:  
  
- Você pode executar seu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo nas versões localizadas apropriadas do Windows.  
  
- Você pode definir a <xref:System.Threading.Thread.CurrentUICulture%2A> propriedade programaticamente em seu aplicativo. (Essa propriedade deve ser definida antes de você chamar o <xref:System.Windows.Forms.Application.Run%2A> método.)  
  
## <a name="see-also"></a>Consulte Também  
 [\<assemblyIdentity> Elementos](../deployment/assemblyidentity-element-clickonce-deployment.md)   
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Globalizando o Windows Forms](https://msdn.microsoft.com/library/72f6cd92-83be-45ec-aa37-9cb8e3ebc3c5)
