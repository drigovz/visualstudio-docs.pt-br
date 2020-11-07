---
title: Localizando aplicativos ClickOnce | Microsoft Docs
description: Saiba mais sobre três maneiras de localizar seu aplicativo ClickOnce para uma versão apropriada para uma cultura específica.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97c4fe8d72cc8e2216ee8f5057d032c071974bf3
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350797"
---
# <a name="localize-clickonce-applications"></a>Localizar aplicativos ClickOnce
A localização é o processo de tornar seu aplicativo apropriado para uma cultura específica. Esse processo envolve a conversão de texto da interface do usuário em uma linguagem específica da região, usando a formatação correta de data e moeda, ajustando o tamanho dos controles em um formulário e espelhando controles da direita para a esquerda, se necessário.

 Localizar o aplicativo resulta na criação de um ou mais assemblies satélite. Cada assembly contém cadeias de caracteres de interface do usuário, imagens e outros recursos específicos de uma determinada cultura. (O arquivo executável principal do seu aplicativo contém as cadeias de caracteres para a cultura padrão para seu aplicativo.)

 Este tópico descreve três maneiras de implantar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo para outras culturas:

- Inclua todos os assemblies satélite em uma única implantação.

- Gere uma implantação para cada cultura, com um único assembly satélite incluído em cada um.

- Baixar assemblies satélites sob demanda.

## <a name="including-all-satellite-assemblies-in-a-deployment"></a>Incluindo todos os assemblies satélite em uma implantação
 Em vez de publicar várias [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantações, você pode publicar uma única [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação que contenha todos os assemblies satélite.

 Esse método é o padrão no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Para usar esse método no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , você não precisa fazer nenhum trabalho adicional.

 Para usar esse método com *MageUI.exe* , você deve definir a cultura do seu aplicativo como **neutra** em *MageUI.exe*. Em seguida, você deve incluir manualmente todos os assemblies satélite em sua implantação. No *MageUI.exe* , você pode adicionar os assemblies satélite usando o botão **popular** na guia **arquivos** do manifesto do aplicativo.

 A vantagem dessa abordagem é que ela cria uma única implantação e simplifica sua história de implantação localizada. Em tempo de execução, o assembly satélite apropriado será usado, dependendo da cultura padrão do sistema operacional Windows do usuário. Uma desvantagem dessa abordagem é que ela baixa todos os assemblies satélite sempre que o aplicativo é instalado ou atualizado em um computador cliente. Se seu aplicativo tiver um grande número de cadeias de caracteres ou se seus clientes tiverem uma conexão de rede lenta, esse processo poderá afetar o desempenho durante a atualização do aplicativo.

> [!NOTE]
> Essa abordagem pressupõe que seu aplicativo ajuste a altura, a largura e a posição de controles automaticamente para acomodar tamanhos de cadeia de caracteres de texto diferentes em diferentes culturas. O Windows Forms contém uma variedade de controles e tecnologias que permitem que você projete seu formulário para torná-lo facilmente localizável, incluindo os <xref:System.Windows.Forms.FlowLayoutPanel> controles e, <xref:System.Windows.Forms.TableLayoutPanel> bem como a <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade.  Consulte também [como oferecer suporte à localização no Windows Forms usando AutoSize e o controle TableLayoutPanel](/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100)).

## <a name="generate-one-deployment-for-each-culture"></a>Gerar uma implantação para cada cultura
 Nessa estratégia de implantação, você gera várias implantações. Em cada implantação, você inclui apenas o assembly satélite necessário para uma cultura específica e marca a implantação como específica para essa cultura.

 Para usar esse método no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , defina a propriedade **idioma de publicação** na guia **publicar** para a região desejada. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o incluirá automaticamente o assembly satélite necessário para a região selecionada e excluirá todos os outros assemblies satélites da implantação.

 Você pode fazer a mesma coisa usando a ferramenta de *MageUI.exe* na Microsoft [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Use o botão **popular** na guia **arquivos** do manifesto do aplicativo para excluir todos os outros assemblies satélite do diretório do aplicativo e, em seguida, defina o campo **cultura** na guia **nome** do manifesto de implantação no *MageUI.exe*. Essas etapas não apenas incluem o assembly satélite correto, mas também definem o `language` atributo no `assemblyIdentity` elemento em seu manifesto de implantação para a cultura correspondente.

 Depois de publicar o aplicativo, você deve repetir essa etapa para cada cultura adicional à qual seu aplicativo dá suporte. Você deve certificar-se de publicar em um diretório de servidor Web ou diretório de compartilhamento de arquivos diferente sempre, porque cada manifesto do aplicativo fará referência a um assembly satélite diferente e cada manifesto de implantação terá um valor diferente para o `language` atributo.

## <a name="download-satellite-assemblies-on-demand"></a>Baixar assemblies satélites sob demanda
 Se você decidir incluir todos os assemblies satélite em uma única implantação, poderá melhorar o desempenho usando o download sob demanda, o que permite marcar assemblies como opcionais. Os assemblies marcados não serão baixados quando o aplicativo for instalado ou atualizado. Você pode instalar os assemblies quando precisar deles chamando o <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> método na <xref:System.Deployment.Application.ApplicationDeployment> classe.

 O download de assemblies satélite sob demanda difere ligeiramente de baixar outros tipos de assemblies sob demanda. Para obter mais informações e exemplos de código sobre como habilitar esse cenário usando o [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] ferramentas para o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consulte [passo a passo: baixando Assemblies de satélite por demanda com a API de implantação do ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md).

 Você também pode habilitar esse cenário no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Consulte também [instruções passo a passo: baixando Assemblies de satélite sob demanda com o ClickOnce Deployment API usando o Designer](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) ou [passo a passo: baixando Assemblies de satélite por demanda com a API de implantação do ClickOnce Usando o Designer](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).

## <a name="testing-localized-clickonce-applications-before-deployment"></a>Testando aplicativos ClickOnce localizados antes da implantação
 Um assembly satélite será usado para um aplicativo Windows Forms somente se a <xref:System.Threading.Thread.CurrentUICulture%2A> Propriedade do thread principal do aplicativo for definida como a cultura do assembly satélite. Os clientes em mercados locais provavelmente já estarão executando uma versão localizada do Windows com a cultura definida para o padrão apropriado.

 Você tem três opções para testar implantações localizadas antes de tornar seu aplicativo disponível para os clientes:

- Você pode executar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo nas versões localizadas apropriadas do Windows.

- Você pode definir a <xref:System.Threading.Thread.CurrentUICulture%2A> propriedade programaticamente em seu aplicativo. (Essa propriedade deve ser definida antes de você chamar o <xref:System.Windows.Forms.Application.Run%2A> método.)

## <a name="see-also"></a>Veja também
- [\<assemblyIdentity> elementos](../deployment/assemblyidentity-element-clickonce-deployment.md)
- [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Globalizar formulários do Windows](/dotnet/framework/winforms/advanced/globalizing-windows-forms)