---
title: 'Walkthrough: baixando assemblies sob demanda com a API de implantação do ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af03329a05501427f6d04d6cddbd637c3311b339
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838471"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Instruções passo a passo: baixando assemblies por demanda com a API de implantação do ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Por padrão, todos os assemblies incluídos em um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo são baixados quando o aplicativo é executado pela primeira vez. No entanto, você pode ter partes do seu aplicativo que são usadas por um pequeno conjunto de usuários. Nesse caso, você deseja baixar um assembly somente quando você cria um de seus tipos. A instrução a seguir demonstra como marcar determinados assemblies em seu aplicativo como "opcional" e como baixá-los usando classes no <xref:System.Deployment.Application> namespace quando o Common Language Runtime (CLR) os exige.  
  
> [!NOTE]
> Seu aplicativo terá que ser executado com confiança total para usar este procedimento.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisará de um dos seguintes componentes para concluir este passo a passos:  
  
- O SDK do Windows. O SDK do Windows pode ser baixado do centro de download da Microsoft.  
  
- Visual Studio.  
  
## <a name="creating-the-projects"></a>Criando os Projetos  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Para criar um projeto que usa um assembly sob demanda  
  
1. Crie um diretório chamado ClickOnceOnDemand.  
  
2. Abra o prompt de comando do SDK do Windows ou o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prompt de comando.  
  
3. Altere para o diretório ClickOnceOnDemand.  
  
4. Gere um par de chaves pública/privada usando o seguinte comando:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5. Usando o bloco de notas ou outro editor de texto, defina uma classe chamada `DynamicClass` com uma única propriedade chamada `Message` .  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
6. Salve o texto como um arquivo chamado `ClickOnceLibrary.cs` ou `ClickOnceLibrary.vb` , dependendo do idioma usado, no diretório ClickOnceOnDemand.  
  
7. Compile o arquivo em um assembly.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8. Para obter o token de chave pública para o assembly, use o seguinte comando:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Crie um novo arquivo usando seu editor de texto e insira o código a seguir. Esse código cria um aplicativo Windows Forms que baixa o assembly ClickOnceLibrary quando necessário.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb#1)]  
  
10. No código, localize a chamada para <xref:System.Reflection.Assembly.LoadFile%2A> .  
  
11. Defina `PublicKeyToken` como o valor que você recuperou anteriormente.  
  
12. Salve o arquivo como `Form1.cs` ou `Form1.vb` .  
  
13. Compile-o em um executável usando o comando a seguir.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Marcando assemblies como opcional  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Para marcar assemblies como opcionais em seu aplicativo ClickOnce usando MageUI.exe  
  
1. Usando MageUI.exe, crie um manifesto do aplicativo conforme descrito em [passo a passos: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Use as seguintes configurações para o manifesto do aplicativo:  
  
    - Nomeie o manifesto do aplicativo `ClickOnceOnDemand` .  
  
    - Na página **arquivos** , na linha ClickOnceLibrary.dll, defina a coluna **tipo de arquivo** como **nenhum**.  
  
    - Na página **arquivos** , na linha ClickOnceLibrary.dll, digite `ClickOnceLibrary.dll` a coluna **grupo** .  
  
2. Usando o MageUI.exe, crie um manifesto de implantação, conforme descrito em [Walkthrough: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Use as seguintes configurações para o manifesto de implantação:  
  
    - Nomeie o manifesto de implantação `ClickOnceOnDemand` .  
  
## <a name="testing-the-new-assembly"></a>Testando o novo assembly  
  
#### <a name="to-test-your-on-demand-assembly"></a>Para testar seu assembly sob demanda  
  
1. Carregue sua [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação em um servidor Web.  
  
2. Inicie o aplicativo implantado com o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] de um navegador da Web, inserindo a URL para o manifesto de implantação. Se você chamar seu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo `ClickOnceOnDemand` e carregá-lo no diretório raiz de adatum.com, sua URL ficaria assim:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3. Quando o formulário principal for exibido, pressione a <xref:System.Windows.Forms.Button> . Você deve ver uma cadeia de caracteres em uma janela de caixa de mensagem que lê "Olá, mundo!".  
  
## <a name="see-also"></a>Consulte Também  
 <xref:System.Deployment.Application.ApplicationDeployment>
