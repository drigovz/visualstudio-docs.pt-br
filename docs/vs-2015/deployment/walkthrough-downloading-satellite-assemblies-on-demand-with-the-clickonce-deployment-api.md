---
title: 'Walkthrough: baixando assemblies satélite sob demanda com a API de implantação do ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a84de037661992d1ee185bea2a70db74dac5e618
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686348"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Instruções passo a passo: baixando assemblies satélite por demanda com a API de implantação do ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Forms aplicativos podem ser configurados para várias culturas por meio do uso de assemblies satélite. Um *assembly satélite* é um assembly que contém recursos de aplicativo para uma cultura diferente da cultura padrão do aplicativo.  
  
 Conforme discutido na [localização de aplicativos ClickOnce](../deployment/localizing-clickonce-applications.md), você pode incluir vários assemblies satélite para várias culturas na mesma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação. Por padrão, o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] baixará todos os assemblies satélite em sua implantação para o computador cliente, embora um único cliente provavelmente exigirá apenas um assembly satélite.  
  
 Este tutorial demonstra como marcar seus assemblies satélite como opcionais e baixar apenas o assembly de que um computador cliente precisa para suas configurações de cultura atuais. O procedimento a seguir usa as ferramentas disponíveis no [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . Você também pode executar essa tarefa no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  Consulte também [instruções passo a passo: baixando Assemblies de satélite sob demanda com o ClickOnce Deployment API usando o Designer](https://msdn.microsoft.com/library/ms366788\(v=vs.110\)) ou [passo a passo: baixando Assemblies de satélite por demanda com a API de implantação do ClickOnce Usando o Designer](https://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
> Para fins de teste, o exemplo de código a seguir define programaticamente a cultura como `ja-JP` . Consulte a seção "próximas etapas" mais adiante neste tópico para obter informações sobre como ajustar esse código para um ambiente de produção.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você saiba como adicionar recursos localizados ao seu aplicativo usando o Visual Studio. Para obter instruções detalhadas, consulte [Walkthrough: localizando Windows Forms](https://msdn.microsoft.com/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Para baixar assemblies satélite sob demanda  
  
1. Adicione o código a seguir ao seu aplicativo para habilitar o download sob demanda de assemblies satélite.  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/CS/Program.cs#1)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/VB/Form1.vb#1)]  
  
2. Gere assemblies satélite para seu aplicativo usando [Resgen.exe (gerador de arquivo de recurso)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
3. Gere um manifesto do aplicativo ou abra o manifesto do aplicativo existente usando MageUI.exe. Para obter mais informações sobre essa ferramenta, consulte [MageUI.exe (manifest Generation and Editing Tool, cliente gráfico)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
4. Clique na guia **arquivos** .  
  
5. Clique no botão de **reticências** (**...**) e selecione o diretório que contém todos os assemblies e arquivos do seu aplicativo, incluindo os assemblies satélite gerados usando Resgen.exe. (Um assembly satélite terá um nome na forma *isoCode*\ApplicationName.resources.dll, em que *isoCode* é um identificador de idioma no formato RFC 1766.)  
  
6. Clique em **popular** para adicionar os arquivos à sua implantação.  
  
7. Marque a caixa de seleção **opcional** para cada assembly satélite.  
  
8. Defina o campo de grupo para cada assembly satélite para seu identificador de idioma ISO. Por exemplo, para um assembly satélite em Japonês, você deve especificar um nome de grupo de download de `ja-JP` . Isso habilitará o código adicionado na etapa 1 para baixar o assembly satélite apropriado, dependendo da configuração de Propriedade do usuário <xref:System.Threading.Thread.CurrentUICulture%2A> .  
  
## <a name="next-steps"></a>Próximas etapas  
 Em um ambiente de produção, provavelmente você precisará remover a linha no exemplo de código que define <xref:System.Threading.Thread.CurrentUICulture%2A> para um valor específico, pois os computadores cliente terão o valor correto definido por padrão. Quando o aplicativo é executado em um computador cliente japonês, por exemplo, <xref:System.Threading.Thread.CurrentUICulture%2A> será `ja-JP` por padrão. Definir esse valor programaticamente é uma boa maneira de testar seus assemblies satélites antes de implantar seu aplicativo.  
  
## <a name="see-also"></a>Consulte Também  
 [Localizando aplicativos ClickOnce](../deployment/localizing-clickonce-applications.md)
