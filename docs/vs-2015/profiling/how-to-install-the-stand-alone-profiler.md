---
title: 'Como: Instalar o criador de perfil independente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b32966dd8a64c4688878ab2843893a1f2a9a3cff
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069660"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Como: Instalar o Profiler autônomo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornece uma linha de comando baseada no criador de perfil autônomo que pode ser executado sem instalar o IDE [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Essa situação ocorre quando um computador não tiver ou não puder ter um ambiente de desenvolvimento instalado. Por exemplo, você não deve instalar um ambiente de desenvolvimento em um servidor Web de produção.  
  
> [!NOTE]
>  Quando você estiver usando o criador de perfil autônomo para coletar dados de desempenho para o site da Web do ASP.NET, a ferramenta de linha [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) é recomendada em vez de [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-install-the-stand-alone-profiler"></a>Para instalar o criador de perfil autônomo  
  
1. Localize o instalador do perfil autônomo (vs_profiler.exe) na mídia de instalação do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no diretório que inclui o caminho do criador de perfil \Standalone e execute-o.  
  
2. Adicione caminhos para vsintr.exe e msdis150.dll ao caminho do sistema.  
  
    > [!NOTE]
    >  Na instalação padrão do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vsinstr.exe e msdis150.dll estão localizados em \Program Files\Visual Studio 10\Team Tools\Performance Tools.  
  
3. No prompt de comando, digite **VSInstr**.  
  
    > [!NOTE]
    >  Se as informações de uso para vsinstr.exe forem exibidas, tudo está configurado corretamente. Se você vir um erro que afirme vsinstr.exe ou uma de suas dependências não for encontrada, certifique-se de que você tenha seus caminhos configurados corretamente, conforme descrito na etapa 2.  
  
4. Configure o servidor de símbolos definindo sua variável **NT_SYMBOL_PATH** como **symsrv\*symsrv.dll\*c:\localcache\*http://msdl.microsoft.com/download/symbols**  
  
5. Depois de configurar o servidor de símbolo usando as variáveis de ambiente do sistema, execute as ferramentas do criador de perfil de linha de comando em um novo prompt de comando. Isso permite que as novas variáveis de ambiente entrem em vigor. Na janela de prompt de comando, digite o seguinte comando:  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    >  Para obter instruções detalhadas sobre como configurar o pacote do servidor de símbolos, confira [Como: Informações de símbolo de referência Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
6. Use a ferramenta [VSPerfReport](../profiling/vsperfreport.md) para serializar os símbolos no arquivo de dados (.vsp) de criação de perfil. Use a opção **VSPerfReport /summary:all /packsymbols**. Se você não tiver símbolos inseridos no arquivo de dados, certifique-se de que tenha o conjunto de variáveis de ambiente NT_SYMBOL_PATH.  
  
## <a name="see-also"></a>Consulte também  
 [Criando perfil na linha de comando](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Passo a passo: Criação de perfil usando amostragem de linha de comando](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [Passo a passo: Linha de comando usando instrumentação de criação de perfil](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Como: Informações de símbolo do Windows de referência](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
