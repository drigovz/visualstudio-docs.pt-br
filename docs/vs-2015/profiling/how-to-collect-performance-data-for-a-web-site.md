---
title: 'Como: Coletar dados de desempenho de um site | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4391f4cf989b51a49b874e6eccdcceb28f609003
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060547"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Como: Coletar dados de desempenho para um Site da Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar o **Assistente de Desempenho** para coletar dados de desempenho para um aplicativo Web do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. É possível criar o perfil de um aplicativo Web que esteja aberto no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou criar um perfil de um site da Web do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] que está localizado no computador local e não aberto no IDE do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
> [!NOTE]
>  O **Assistente de Desempenho** permite que você adicione dados de interação de camadas (TIP), dados de desempenho de JScript ou ambos os dados de criação de perfil coletados. A opção TIP coleta dados de processos do servidor. A criação de perfil do JScript coleta dados de scripts que são executados em um site da Web local ou remoto. Na maioria dos casos, você deve escolher apenas uma das opções.  
  
 Dependendo das configurações de Permissões de Acesso do Usuário que um administrador tenha disponibilizado, um usuário individual pode ter ou não a permissão de segurança para criar uma sessão de criador de perfil no computador que hospeda o processo ASP.NET. Os exemplos a seguir ilustram possíveis diferenças entre os usuários:  
  
- Alguns usuários podem acessar recursos de criação de perfil avançados quando o Administrador tiver configurado o início do driver e do serviço.  
  
- Os usuários do domínio podem acessar apenas as amostras de criação de perfil.  
  
- Alguns usuários podem negar acesso à criação de perfil para todos os outros usuários.  
  
  Para obter mais informações, consulte [Criação de perfil e segurança do Windows Vista](../profiling/profiling-and-windows-vista-security.md) e as opções de administração em [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-profile-a-web-site-project"></a>Para criar o perfil de um projeto de site da Web  
  
1. Abra o projeto Web do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] em [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] ou [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].  
  
2. No menu **Analisar**, clique em **Iniciar o Assistente de Desempenho**.  
  
3. Na primeira página do assistente, selecione um método de criação de perfil e, em seguida, clique em **Avançar**. Para obter mais informações sobre métodos de criação de perfil, consulte [Noções básicas sobre métodos de coleta de desempenho](../profiling/understanding-performance-collection-methods.md). Observe que o método de criação de perfil do visualizador de simultaneidade não está disponível para aplicativos Web.  
  
4. Na lista suspensa **Qual aplicativo você deseja direcionar para a criação de perfil?**, certifique-se de que o projeto atual esteja selecionado e, em seguida, clique em **Avançar**.  
  
5. Na terceira página do assistente, você pode adicionar dados de criação de perfil de interação de camada (TIP), dados do JavaScript em execução nas páginas da Web ou ambos.  
  
    - Para coletar a interação da camada, selecione a caixa de seleção **Habilitar Criação de Perfil de Interação de Camada**.  
  
    - Para coletar dados do JavaScript em execução nas páginas da Web, selecione a caixa de seleção **Criar perfil de JavaScript**.  
  
6. Clique em **Avançar**.  
  
7. Na quarta página do assistente, clique em **Concluir**.  
  
8. Uma sessão de desempenho é criada para o aplicativo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] e o site da Web é iniciado no navegador. Execute a funcionalidade para qual deseja criar o perfil e, em seguida, feche o navegador.  
  
     O criador de perfil gera o arquivo de dados e demonstra a exibição dos dados de Resumo na janela principal do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
### <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Para criar o perfil de um site da Web sem abrir um projeto no Visual Studio  
  
1. Abra [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] ou [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].  
  
2. No menu **Analisar**, clique em **Iniciar o Assistente de Desempenho**.  
  
3. Na primeira página do assistente, selecione um método de criação de perfil e, em seguida, clique em **Avançar**. Para obter mais informações, consulte [Noções Básicas sobre Métodos de Coleta de Desempenho](../profiling/understanding-performance-collection-methods.md).  
  
4. Na segunda página do assistente, selecione a opção **Criar Perfil de um aplicativo ASP.NET ou JavaScript** e, em seguida, clique em **Avançar**.  
  
5. Na caixa **Qual URL ou Caminho executará seu aplicativo Web** na terceira página do assistente, insira a URL para a home page do aplicativo e, em seguida, clique em **Avançar**.  
  
   - Para um site baseado em servidor (IIS), digite uma URL como **http://localhost/MySite/default.aspx**. Isso faz com que o aplicativo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] no computador local na raiz do aplicativo do MySite tenha seu perfil criado e a página default.aspx nesse site seja iniciada no Internet Explorer para iniciar a sessão.  
  
   - Para um site da Web baseado em um arquivo, digite um caminho como file///**c:\WebSites\MySite\default.aspx**. Isso faz com que o aplicativo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] localizado em c:\webSites\MySite tenha seu perfil criado e a página http://localhost:nnnn/MySite/default.aspx seja iniciada no Internet Explorer para iniciar a sessão.  
  
   - Para sites externos que você deseja coletar dados de JavaScript, digite a URL, por exemplo, http:\//www.contoso.com.  
  
     Para obter mais informações, exiba as páginas de propriedades para um binário de destino de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
6. Na terceira página do assistente, você pode adicionar dados de criação de perfil de interação de camada (TIP), dados do JavaScript em execução nas páginas da Web ou ambos.  
  
   - Para coletar a interação da camada, selecione a caixa de seleção **Habilitar Criação de Perfil de Interação de Camada**.  
  
   - Para coletar dados do JavaScript em execução nas páginas da Web, selecione a caixa de seleção **Criar perfil de JavaScript**.  
  
7. Clique em **Avançar**.  
  
8. Na quarta página do assistente, clique em **Concluir**.  
  
9. Uma sessão de desempenho é criada para o aplicativo ASP.NET e o site da Web é iniciado no navegador. Execute a funcionalidade para qual deseja criar o perfil e, em seguida, feche o navegador.  
  
     O criador de perfil gera o arquivo de dados e demonstra a exibição dos dados de Resumo na janela principal do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Visões gerais](../profiling/overviews-performance-tools.md)   
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)   
 [Noções Básicas sobre Valores de Dados de Instrumentação](../profiling/understanding-instrumentation-data-values.md)   
 [Noções básicas sobre valores de dados de amostragem](../profiling/understanding-sampling-data-values.md)
