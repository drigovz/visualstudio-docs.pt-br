---
title: Modelo de projeto VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2386f1be805f6347fc32fba4ee8bfe57c8602329
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838664"
---
# <a name="vsix-project-template"></a>Modelo de projeto do VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar o modelo de projeto VSIX para encapsular uma ou mais extensões do Visual Studio em um projeto VSIX e, em seguida, publicar o pacote no site da [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .  
  
 A implantação do VSIX dá suporte a VSPackages, assemblies, componentes do MEF, modelos de projeto, modelos de item, controles de caixa de ferramentas e tipos de extensão personalizados.  
  
> [!NOTE]
> Para usar projetos VSIX, você deve instalar o SDK do Visual Studio. Para obter mais informações sobre o SDK do Visual Studio, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>Onde encontrar o modelo de projeto VSIX  
 O modelo de projeto VSIX está disponível na caixa de diálogo **novo projeto** . Expanda o nó **Visual Basic** ou o nó do **Visual C#** e escolha **extensibilidade**.  
  
> [!TIP]
> Você deve certificar-se de que .NET Framework 4,5 ou superior esteja especificado na lista suspensa na parte superior da caixa de diálogo **novo projeto** .  
  
## <a name="uses-of-the-vsix-project-template"></a>Usos do modelo de projeto VSIX  
 O modelo de projeto VSIX tem dois usos principais:  
  
- Para implantar modelos de projeto, modelos de item e outras extensões que ainda não têm suporte ao VSIX.  
  
- Para encapsular as saídas de várias extensões em um pacote de implantação.  
  
  Você não precisa usar o modelo de projeto VSIX para implantar VSPackages ou outros tipos de extensões que já têm suporte ao VSIX.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Empacotando uma extensão em um projeto VSIX vazio  
 Você pode empacotar uma extensão existente ou uma extensão que ainda não tem suporte a VSIX, encapsulando-a em um projeto VSIX vazio. A extensão a ser encapsulada deve ser de um tipo com suporte do [esquema VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Para empacotar uma extensão usando um projeto VSIX  
  
1. Compile os projetos que compõem sua extensão.  
  
2. Crie um projeto VSIX usando o modelo de **projeto VSIX** .  
  
     Source. Extension. vsixmanifest é aberto no **Designer de manifesto**.  
  
3. Na guia **ativos** , escolha o botão **novo** .  
  
     A caixa de diálogo **Adicionar novo ativo** é exibida.  
  
4. Na lista **tipo** , escolha o tipo de extensão a ser adicionado.  
  
5. Para adicionar uma extensão ou elemento de conteúdo que está incluído na solução atual (por exemplo, um modelo de item ou um assembly compilado), execute as seguintes etapas:  
  
    1. Na lista **origem** , escolha **um projeto na solução atual**.  
  
    2. Na lista **projeto** , escolha o nome da extensão.  
  
    3. Na caixa **Inserir nesta pasta** , digite o nome de uma pasta na qual o ativo será inserido e, em seguida, escolha o botão **OK** .  
  
6. Para adicionar uma extensão ou elemento de conteúdo que não está incluído na solução atual, execute as seguintes etapas:  
  
    1. Na caixa de listagem **origem** , escolha **arquivo no sistema de arquivos**.  
  
    2. No campo **caminho** , insira o caminho completo para o arquivo de extensão compilado ou compactado ou use o botão **procurar** para navegar até o arquivo.  
  
    3. Na caixa **Inserir nesta pasta** , digite o nome de uma pasta na qual o ativo será inserido e, em seguida, escolha o botão **OK** .  
  
7. Se você quiser que seu pacote inclua extensões adicionais, adicione-as da mesma maneira.  
  
8. Compile a solução.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Cria um arquivo. vsix que contém um arquivo de manifesto do VSIX, um arquivo [Content_Types]. xml e todos os ativos de extensão que você adicionou ao projeto.  
  
## <a name="see-also"></a>Consulte Também  
 [Referência do esquema de extensão do VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Localizando e usando extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
