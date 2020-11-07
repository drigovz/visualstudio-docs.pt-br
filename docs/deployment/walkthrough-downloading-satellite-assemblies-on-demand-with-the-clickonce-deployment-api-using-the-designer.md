---
title: Baixar o assembly satélite sob demanda usando o designer do ClickOnce
description: Saiba como marcar assemblies satélite como opcionais usando o designer e baixar apenas o assembly de que um computador cliente precisa para suas configurações de cultura atuais.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b6b57faf01878dc5aff708f0aca47707bf6e48c
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350329"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Walkthrough: baixar assemblies satélite sob demanda com a API de implantação do ClickOnce usando o designer
Windows Forms aplicativos podem ser configurados para várias culturas por meio do uso de assemblies satélite. Um *assembly satélite* é um assembly que contém recursos de aplicativo para uma cultura diferente da cultura padrão do aplicativo.

 Conforme discutido na [localização de aplicativos ClickOnce](../deployment/localizing-clickonce-applications.md), você pode incluir vários assemblies satélite para várias culturas na mesma [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação. Por padrão, o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] baixará todos os assemblies satélite em sua implantação para o computador cliente, embora um único cliente provavelmente exigirá apenas um assembly satélite.

 Este tutorial demonstra como marcar seus assemblies satélite como opcionais e baixar apenas o assembly de que um computador cliente precisa para suas configurações de cultura atuais.

> [!NOTE]
> Para fins de teste, os exemplos de código a seguir programaticamente definem a cultura como `ja-JP` . Consulte a seção "próximas etapas" mais adiante neste tópico para obter informações sobre como ajustar esse código para um ambiente de produção.

### <a name="to-mark-satellite-assemblies-as-optional"></a>Para marcar assemblies satélite como opcionais

1. Compile o projeto. Isso irá gerar assemblies satélite para todas as culturas para as quais você está localizando.

2. Clique com o botão direito do mouse no nome do projeto em Gerenciador de Soluções e clique em **Propriedades**.

3. Clique na guia **publicar** e, em seguida, clique em **arquivos de aplicativo**.

4. Marque a caixa de seleção **Mostrar todos os arquivos** para exibir assemblies satélite. Por padrão, todos os assemblies satélite serão incluídos na sua implantação e estarão visíveis nessa caixa de diálogo.

     Um assembly satélite terá um nome no formulário *\<isoCode>\ApplicationName.resources.dll* , em que \<isoCode> é um identificador de idioma no formato RFC 1766.

5. Clique em **novo** na lista de **grupos de download** para cada identificador de idioma. Quando for solicitado um nome de grupo de download, insira o identificador de idioma. Por exemplo, para um assembly satélite em Japonês, você deve especificar o nome do grupo de download `ja-JP` .

6. Feche a caixa de diálogo **arquivos de aplicativo** .

### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>Para baixar assemblies satélite sob demanda em C\#

1. Abra o arquivo *Program.cs* . Se você não vir esse arquivo em Gerenciador de Soluções, selecione seu projeto e, no menu **projeto** , clique em **Mostrar todos os arquivos**.

2. Use o código a seguir para baixar o assembly satélite apropriado e iniciar o aplicativo.

     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]

### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Para baixar assemblies satélite sob demanda no Visual Basic

1. Na janela **Propriedades** do aplicativo, clique na guia **aplicativo** .

2. Na parte inferior da página da guia, clique em **Exibir eventos do aplicativo**.

3. Adicione as seguintes importações ao início do arquivo *ApplicationEvents. vb* .

     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]

4. Adicione o código a seguir à classe `MyApplication` .

     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]

## <a name="next-steps"></a>Próximas etapas
 Em um ambiente de produção, provavelmente você precisará remover a linha nos exemplos de código que define <xref:System.Threading.Thread.CurrentUICulture%2A> para um valor específico, pois os computadores cliente terão o valor correto definido por padrão. Quando o aplicativo é executado em um computador cliente japonês, por exemplo, <xref:System.Threading.Thread.CurrentUICulture%2A> será `ja-JP` por padrão. Configurá-lo programaticamente é uma boa maneira de testar seus assemblies satélites antes de implantar seu aplicativo.

## <a name="see-also"></a>Veja também
- [Walkthrough: baixar assemblies satélite sob demanda com a API de implantação do ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)
- [Localizar aplicativos ClickOnce](../deployment/localizing-clickonce-applications.md)
