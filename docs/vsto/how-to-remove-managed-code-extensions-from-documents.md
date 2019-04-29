---
title: 'Como: Remover extensões de código gerenciado de documentos'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 438658af3f182ea732d0fefef0f5a5d6ecbefa03
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961586"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Como: Remover extensões de código gerenciado de documentos
  Você poderá remover programaticamente o assembly de personalização de um documento ou pasta de trabalho que faz parte de uma personalização no nível de documento para o Microsoft Office Word ou Microsoft Office Excel. Os usuários podem, em seguida, abra os documentos e exibir o conteúdo, mas não aparecerá nenhuma interface do usuário personalizada (UI) adicionar aos documentos e seu código não será executado.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Você pode remover o assembly de personalização, usando uma da `RemoveCustomization` métodos fornecidos pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Qual método você usa depende se você deseja remover a personalização em tempo de execução (ou seja, executando o código na personalização enquanto a palavra documento ou pasta de trabalho do Excel é aberta), ou se você quiser remover a personalização de um documento fechado ou um documento que i s em um servidor que não tenha o Microsoft Office instalado.

 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração em vídeo relacionada, consulte [como: Anexar ou desanexar um Assembly do VSTO a partir de um documento do Word? ](http://go.microsoft.com/fwlink/?LinkId=136782).

## <a name="to-remove-the-customization-assembly-at-runtime"></a>Para remover o assembly de personalização em tempo de execução

1. No seu código de personalização, chame o <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> método (para o Word) ou o <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> método (para Excel). Esse método deve ser chamado somente depois que a personalização não for mais necessário.

     Em que você chamar esse método em seu código depende de como sua personalização é usada. Por exemplo, se os clientes usam os recursos da sua personalização até que eles estejam prontos para enviar um documento para outros clientes que precisam apenas o documento em si (não a personalização), você pode fornecer algumas interfaces do usuário que chama `RemoveCustomization` quando o cliente clica nele. Como alternativa, se sua personalização preenche o documento com os dados quando ele é aberto pela primeira vez, mas a personalização não fornece outros recursos que são acessados diretamente por clientes, em seguida, você pode chamar RemoveCustomization assim que a personalização conclui a inicialização do documento.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Para remover o assembly de personalização de um documento fechado ou um documento em um servidor

1. Em um projeto que não requer o Microsoft Office, como um aplicativo de console ou um projeto do Windows Forms, adicione uma referência para o *ServerDocument* assembly.

2. Adicione o seguinte **importações** ou **usando** instrução na parte superior do seu arquivo de código.

     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]

3. Chamar estático <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> método da <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> de classe e especifique o caminho do documento de solução para o parâmetro.

     O exemplo de código a seguir pressupõe que você está removendo a personalização de um documento chamado *WordDocument1.docx* que está na área de trabalho.

     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]

4. Compile o projeto e executar o aplicativo no computador em que você deseja remover a personalização. O computador deve ter o Visual Studio 2010 Tools para Office runtime instalado.

## <a name="see-also"></a>Consulte também
- [Gerenciar documentos em um servidor usando a classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Como: Anexar extensões de código gerenciado para documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
