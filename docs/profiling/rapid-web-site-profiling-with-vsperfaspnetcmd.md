---
title: Criação de perfil do site rápida com VSPerfASPNETCmd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fff2486c4197cbbe28c3b5deb0099e264805e12b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771686"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Criação rápida de perfil de site com VSPerfASPNETCmd

A ferramenta de linha de comando **VSPerfASPNETCmd** permite criar facilmente o perfil de aplicativos Web do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Em comparação com a ferramenta de linha de comando [VSPerfCmd](../profiling/vsperfcmd.md), as opções são reduzidas, nenhuma variável de ambiente precisa ser definida e não é necessário reinicializar o computador. Usar **VSPerfASPNETCmd** é o método preferencial para a criação de perfil com o criador de perfil autônomo. Para obter mais informações, [consulte Como: Instalar o profiler autônomo](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos UWP também requerem novas técnicas de coleta. Consulte [ferramentas de desempenho em aplicativos windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Em alguns cenários, tais como coletar dados de simultaneidade ou pausar e retomar a criação de perfil, o uso de **VSPerfCmd** é o método preferencial de criação de perfil.

> [!NOTE]
> Para obter o caminho para as ferramentas de criação de perfil, confira [Especificar o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Em computadores de 64 bits, as versões de 64 e de 32 bits das ferramentas estão disponíveis. Para usar ferramentas de linha de comando do criador de perfil, você precisa adicionar o caminho das ferramentas à variável de ambiente PATH da janela de Prompt de Comando ou adicioná-lo ao próprio comando.

## <a name="profile-an-aspnet-application"></a>Criar o perfil de um aplicativo ASP.NET

Para criar o perfil de um aplicativo Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], digite um dos comandos descritos nas seções a seguir. O site é iniciado e abre o criador de perfil para coletar dados. Exercite seu aplicativo e, em seguida, feche o navegador. Para parar a criação de perfil, **pressione** a tecla Enter na janela de solicitação de comando.

> [!NOTE]
> Por padrão, o prompt de comando não retorna após um comando **vsperfaspnetcmd**. Você pode usar a opção **/nowait** para forçar o prompt de comando a retornar. Confira [Usar a opção /NoWait](#use-the-nowait-option).

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Para coletar estatísticas do aplicativo usando o método de amostragem
 A amostragem é o método de criação de perfil de padrão da ferramenta **VSPerfASPNETCmd** e não precisa ser especificada na linha de comando. A seguinte linha de comando coleta estatísticas de aplicativo do aplicativo Web especificado:

 **vsperfaspnetcmd**  *websiteUrl*

 Um exemplo de *websiteUrl* hospedado no servidor local pode ser *http://localhost/MySite/default.aspx*. Um exemplo de um *http://www.contoso.com*site externo é . Para obter mais informações, confira as URLs de exemplo em [Para criar o perfil de um site sem abrir um projeto no Visual Studio](how-to-collect-performance-data-for-a-web-site.md#to-profile-a-web-site-without-opening-a-project-in-visual-studio).

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Para coletar dados de tempo detalhados usando o método de instrumentação

Use a seguinte linha de comando para coletar dados de tempo detalhados de um aplicativo Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilado dinamicamente:

**vsperfaspnetcmd /trace**  *websiteUrl*

Se você quiser traçar o perfil comcompilado estáticamente . arquivos *dll* em seu aplicativo web, você deve instrumentalar os arquivos usando a ferramenta de linha de comando [VSInstr.](../profiling/vsinstr.md) O comando vsperfaspnetcmd /trace incluirá dados dos arquivos instrumentados.

## <a name="to-collect-net-memory-data"></a>Para coletar dados de memória do .NET

A opção **/Memory** coleta dados sobre a alocação de objetos na memória do .NET e pode coletar dados sobre o tempo de vida desses objetos. A coleta de dados de alocação é o modo padrão das opções de dados **/Memory** e não precisa ser especificado na linha de comando.

 **vsperfaspnetcmd /memory** *websiteUrl*

 Use o parâmetro **Tempo de vida** para coletar dados de tempo de vida do objeto além dos dados de alocação:

 **vsperfaspnetcmd /memory:lifetime** *websiteUrl*

 Você também pode usar a opção **/Trace** para incluir informações detalhadas de tempo com os dados de memória do .NET:

 **vsperfaspnetcmd /memory**[**:lifetime**] **/trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Para coletar dados de interação entre camadas

> [!WARNING]
> Os dados de TIP (criação de perfil de interação de camadas) podem ser coletados usando qualquer edição do Visual Studio. No entanto, os dados de criação de perfil de interação de camadas só podem ser exibidos no Visual Studio Enterprise.
>
> Para coletar dados TIP no Windows 8 ou Windows Server 2012, você deve usar a opção de instrumentação (**/trace**).

Para coletar dados de interação entre camadas com os dados de amostragem:

**vsperfaspnetcmd /tip** `websiteUrl`

Para coletar dados de interação entre camadas com os dados de instrumentação:

**vsperfaspnetcmd /trace /tip** *websiteUrl*

Para coletar dados de interação entre camadas com os dados de memória de .NET:

**vsperfaspnetcmd /memory**[**:lifetime**] **/tip**_websiteUrl_

## <a name="use-the-nowait-option"></a>Use a opção /NoWait

Por padrão, o prompt de comando não retorna após um comando **vsperfaspnetcmd**. Você pode usar a opção de sintaxe a seguir para forçar o prompt de comando a retornar. Em seguida, você pode executar outras operações na janela do prompt de comando. Para finalizar a criação de perfil, use a opção **/shutdown** em um comando **vsperfaspnetcmd**.

Para iniciar a criação de perfil:

**vsperfaspnetcmd** [*/Options*] **/nowait**_websiteUrl_

Para encerrar a criação de perfil:

**vsperfaspnetcmd /shutdown** *websiteUrl*

## <a name="additional-options"></a>Opções adicionais

Você pode adicionar qualquer uma das seguintes opções aos comandos listados anteriormente nesta seção, exceto o **vsperfaspnetcmd /shutdown**.

|Opção|Descrição|
|------------|-----------------|
|**/Saída:**`VspFile`|Por padrão, os dados de criação de perfil (.* vsp*) arquivo é criado no diretório atual com o nome do arquivo **PerformanceReport.vsp**. Use a opção /output para especificar um local diferente, nome do arquivo diferente ou ambos.|
|**/PackSymbols:Off**|Por padrão, VsPerfASPNETCmd insere símbolos (nomes de função, de parâmetro e assim por diante) no arquivo .*vsp*. Inserir os símbolos pode tornar o arquivo de dados de criação de perfil muito grande. Se você tiver acesso ao . *pdb* arquivos que contêm os símbolos quando você analisa os dados, use a opção /packsymbols:off para desativar a incorporação dos símbolos.|
