---
title: Dados particulares para relatórios de problemas
ms.date: 06/21/2018
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e87f35778b8aec615410312c0eb7373d4e9969f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75775883"
---
# <a name="developer-community-data-privacy"></a>Privacidade de dados da Comunidade de Desenvolvedores

Por padrão, todas as informações nos relatórios de problema na [Comunidade de Desenvolvedores](https://developercommunity.visualstudio.com/), inclusive todos os comentários e as respostas, ficam visíveis publicamente. Isso é útil porque permite que toda a comunidade veja os problemas, as soluções e as soluções alternativas que outros usuários descobriram. No entanto, se você está preocupado com a privacidade dos dados ou da identidade, há opções para isso.

## <a name="identity-privacy"></a>Privacidade da identidade

Se você está preocupado com a revelação da sua identidade, [crie uma conta Microsoft](https://signup.live.com/) que não divulgue todos os detalhes sobre você. Use essa conta para criar seu relatório.

## <a name="data-privacy"></a>Privacidade dos dados

Se você está preocupado com a privacidade dos dados, não coloque nada que deseja manter particular no título ou no conteúdo do relatório inicial, que sempre é público. Nesse caso, crie o relatório e, em seguida, observe que você enviará detalhes de forma particular em um comentário separado. Depois de criar o relatório do problema, especifique quem pode ver as respostas e os anexos:

1. No relatório que você criou, escolha **Adicionar comentário** para criar uma descrição particular do problema.

2. No editor de resposta, use o controle abaixo dos botões **Enviar** e **Cancelar** para especificar a audiência da resposta. Escolha **Visível por moderadores e o cartaz original** para limitar a visibilidade aos funcionários da Microsoft e a você mesmo.

   ![Controle de privacidade na Comunidade de Desenvolvedores](media/developer-community-privacy-control.png)

   Somente as pessoas que você especifica podem ver o comentário e as imagens, os links ou o código incluídos nele. Todas as respostas no comentário têm a mesma visibilidade que o comentário original. Isso é verdadeiro mesmo quando o controle de privacidade nas respostas não mostra corretamente o status de visibilidade restrito.

3. Adicione a descrição e quaisquer outras informações, imagens e anexos de arquivo necessários para a reprodução. Escolha o botão **Enviar** para enviar essas informações em particular.

   > [!NOTE]
   > Há um limite de 2 GB para arquivos anexados e de no máximo 10 arquivos. Se você precisar carregar um arquivo maior, envie um novo relatório de problema ou solicite uma URL de upload a um funcionário da Microsoft em um comentário particular.

Para manter sua privacidade e manter informações confidenciais fora da exibição pública, tome cuidado para manter todas as interações com a Microsoft em respostas em um comentário com restrição de visibilidade. Respostas a outros comentários podem gerar a divulgação acidental de informações confidenciais.

## <a name="data-we-collect"></a>Dados que coletamos

Quando a ação **Relatar um problema** é iniciada com o Instalador do Visual Studio, nós coletamos o log de instalação mais recente.

Quando a ação **Relatar um problema** é iniciada com o Visual Studio, nós coletamos um ou mais dos seguintes tipos de dados:

- Entradas do Watson e do .NET do log de eventos

- Arquivo de log de atividades na memória do Visual Studio

- Arquivos do PerfWatson, se a coleção do Watson estiver habilitada

- Arquivos de log do LiveShare, caso existam

- Arquivos de log do Xamarin, caso existam

- Arquivos de log do Nuget, caso existam

- Arquivos de log do depurador da Web, caso existam

- Logs do hub de serviço e logs de erro da MEF, caso existam

- Logs do Python, caso existam

- Windows Forms logs, se eles existem

- Uma captura de tela, caso você escolha incluí-la

- Dados de gravação, caso você escolha incluir gravações, como:

  - Etapas para reproduzir o problema

  - Arquivo de rastreamento de ETL

  - Arquivo de despejo

> [!NOTE]
> Registrar arquivos, capturas de tela e gravar dados que você envia pode aumentar significativamente a capacidade da Microsoft de entender e responder ao seu problema.  Por isso recomendamos incluí-los. Para proteger sua privacidade, quaisquer arquivos de log anexados, capturas de tela e dados de gravação são enviados apenas para a Microsoft quando você fornece permissão enviando o relatório de problemas com o qual eles estão incluídos. Você pode ver quais arquivos estão incluídos na etapa 'Resumo' da janela 'Relatar um problema' antes de enviar o relatório. Você pode excluir arquivos de registro do sistema do relatório deschecando 'Anexar registros do sistema' na etapa 'Resumo'. Para referência, consulte a captura de tela a seguir. 
  > ![Relatar um problema - Resumo dos registros coletados](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>Confira também

- [Como relatar um problema com o Visual Studio](how-to-report-a-problem-with-visual-studio.md)
- [Privacidade de dados do relatório de problema do C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)
