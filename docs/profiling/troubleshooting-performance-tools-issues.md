---
title: Solução de problemas de ferramentas de desempenho | Microsoft Docs
description: Saiba mais sobre vários que você pode enfrentar ao solucionar problemas de ferramentas de desempenho, por exemplo, quando nenhum dado é coletado pelas ferramentas de criação de perfil.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d371384d70c6a6a7a57620839eca2c41c292d0b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922044"
---
# <a name="troubleshoot-performance-tools-issues"></a>Solução de problemas das ferramentas de desempenho
Você pode ter um dos seguintes problemas ao usar as ferramentas de criação de perfil:

- [Nenhum dado é coletado pelas ferramentas de criação de perfil](#no-data-is-collected-by-the-profiling-tools)

- [As Exibições de Desempenho e os relatórios exibem números para nomes de função](#performance-views-and-reports-display-numbers-for-function-names)

## <a name="no-data-is-collected-by-the-profiling-tools"></a>Nenhum dado é coletado pelas ferramentas de criação de perfil
 Depois que você analisa um aplicativo, um arquivo de dados de criação de perfil (.*vsp*) não é criado e você recebe o seguinte aviso na janela de **Saída** ou na janela Comando:

 PRF0025: não foram coletados dados.

 Esse problema pode ser causado por vários motivos:

- Um processo para o qual foi criado um perfil usando a amostragem ou o método de memória .NET inicia um processo filho que se torna o processo que executa o trabalho do aplicativo. Por exemplo, alguns aplicativos leem a linha de comando para determinar se foram iniciados como um aplicativo do Windows ou um aplicativo de linha de comando. Se um aplicativo do Windows foi solicitado, o processo original iniciará um novo processo configurado como um aplicativo do Windows e o processo original será encerrado. Como as ferramentas de criação de perfil não coletam dados automaticamente para processos filho, nenhum dado é coletado.

     Para coletar dados de criação de perfil nessa situação, anexe o criador de perfil ao processo filho em vez de iniciar o aplicativo com o criador de perfil. Para obter mais informações, confira [Como anexar ferramentas de desempenho aos processos em execução e desanexá-las](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) e [Attach (VSPerfCmd)](../profiling/attach.md)

## <a name="performance-views-and-reports-display-numbers-for-function-names"></a>As exibições de desempenho e os relatórios exibem números para nomes de função
 Depois de criar o perfil de um aplicativo, você verá números em vez de nomes de função em exibições e relatórios.

 Esse problema é causado pela incapacidade do mecanismo de análise das Ferramentas de Criação de Perfil em encontrar os arquivos .*pdb* que contêm as informações de símbolo que mapeiam as informações de código-fonte, como nomes de função e números de linha, para o arquivo compilado. Por padrão, o compilador cria o arquivo .*pdb* quando o arquivo de aplicativo é compilado. Uma referência ao diretório local do arquivo .*pdb* é armazenada no aplicativo compilado. O mecanismo de análise busca no diretório referenciado pelo arquivo .*pdb* e, em seguida, no arquivo que atualmente contém o arquivo de aplicativo. Se o arquivo .*pdb* não é encontrado, o mecanismo de análise usa os deslocamentos de função, em vez dos nomes de função.

 Você pode corrigir o problema em uma das duas maneiras:

- Encontre os arquivos .*pdb* e coloque-os no mesmo diretório dos arquivos de aplicativo.

- Insira as informações de símbolo no arquivo de dados de criação de perfil (.*vsp*). Para obter mais informações, confira [Salvar informações de símbolo com arquivos de dados de desempenho](../profiling/saving-symbol-information-with-performance-data-files.md).

> [!NOTE]
> O mecanismo de análise exige que o arquivo .*pdb* tenha a mesma versão do arquivo de aplicativo compilado. Um arquivo .*pdb* de um build anterior ou posterior do arquivo de aplicativo não funcionará.
