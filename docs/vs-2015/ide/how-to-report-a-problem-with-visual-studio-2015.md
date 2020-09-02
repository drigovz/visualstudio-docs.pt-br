---
title: Como relatar um problema com o Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
ms.assetid: 24ecb76e-b7ad-432d-88ab-d9849963465d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db9267fe9f06569dadea240e5d78c8b35c84b8c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386544"
---
# <a name="how-to-report-a-problem-with-visual-studio-2015"></a>How to Report a Problem with Visual Studio 2015 (Como relatar um problema com o Visual Studio 2015)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obter a documentação mais recente sobre Visual Studio, confira [Como relatar um problema no Visual Studio](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

Se você encontrar um problema com o Visual Studio 2015, gostaríamos de saber sobre isso para que possamos diagnosticá-lo e corrigi-lo.  Usando a ferramenta **Relatar um Problema**, você pode coletar informações detalhadas sobre o problema e enviá-las à Microsoft com apenas alguns cliques de botão.

A Microsoft respeita sua privacidade. Para obter informações sobre como tratamos os dados que você nos envia, consulte a [Política de privacidade da família de produtos do Microsoft Visual Studio](https://www.visualstudio.com/dn948229).

## <a name="open-the-report-a-problem-tool"></a>Abrir a ferramenta Relatar um Problema

Clique no ícone de comentários do usuário ao lado de **Início Rápido** na barra de título ou clique em **Ajuda > Enviar Comentários > Relatar um Problema**.

![Relatar um item de menu com problema](../ide/media/report-a-problem-menu-item.png "Relatar um item de menu com problema")

## <a name="describe-the-problem"></a>Descrever o problema

### <a name="describe_the_problem"></a>

1. Forneça um título descritivo para o problema que nos ajudará a roteá-lo para a equipe correta no Visual Studio.

2. Forneça todos os detalhes adicionais e, se possível, as etapas para reproduzir o problema.

3. Escolha uma área de problema no menu suspenso. Se você não tiver certeza, faça a melhor suposição.

   ![Relatar uma caixa de diálogo de problema](../ide/media/report-a-problem-dialog.png "Relatar uma caixa de diálogo de problema")

## <a name="provide-a-screenshot-optional"></a>Fornecer uma captura de tela (opcional)

Escolha **Incluir uma captura de tela** para enviar sua tela atual à Microsoft. A ferramenta permite que você recorte a imagem para mostrar apenas a parte da tela que mostra o problema. Você pode anexar capturas de tela adicionais ou outros arquivos clicando no botão **Anexar Arquivos Adicionais**.

## <a name="provide-a-trace-and-heap-dump-optional"></a>Fornecer um despejo de heap e rastreamento (opcional)

### <a name="provide_a_trace_and_heap_dump"></a>

1. Os arquivos de despejo de heap e rastreamento são muito úteis para nos ajudar a diagnosticar problemas.   Apreciamos muito quando você usa a ferramenta Relatar um Problema para registrar as etapas de reprodução e enviar os dados para a Microsoft.

2. Clique na divisa ao lado **Registrar suas ações para reproduzir o problema**. Se o problema estiver fazendo com que o Visual Studio pare de responder ou falhe, abra outra instância do Visual Studio e selecione-o na exibição de lista.

3. Clique em **Iniciar Gravação** e execute as etapas que reproduzem o problema. Quando terminar, clique no botão **Parar Gravação** na janela flutuante.

4. Aguarde alguns minutos para o Visual Studio coletar e compactar as informações gravadas. A caixa de diálogo terá uma aparência semelhante a essa quando o processo de coleção for concluído:

     ![Registrar um arquivo de rastreamento](../ide/media/record-a-trace-file.png "Registrar um arquivo de rastreamento")

## <a name="describe-the-workaround-if-there-is-one"></a>Descrever a solução alternativa, se houver uma

Se você conseguir contornar o problema, descreva a solução alternativa na caixa de edição fornecida para essa finalidade. Isso nos ajuda não apenas a diagnosticar o problema, mas também a ajudar outros usuários que podem ter o mesmo problema.

## <a name="submit-the-report"></a>Enviar o relatório

Clique no botão Enviar para enviar seu relatório, juntamente com as imagens e os arquivos de despejo ou de rastreamento. Se o botão **Enviar** estiver esmaecido, certifique-se de que você forneceu um título e uma descrição.

## <a name="see-also"></a>Consulte Também

- [Fale conosco](../ide/talk-to-us.md)
