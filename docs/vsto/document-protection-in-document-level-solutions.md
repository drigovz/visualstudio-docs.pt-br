---
title: Proteção do documento em soluções de nível de documento
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b83715574ca9c5612e28f9097a1fcb378f298e1a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862779"
---
# <a name="document-protection-in-document-level-solutions"></a>Proteção do documento em soluções de nível de documento
  Você pode usar os recursos de proteção do Microsoft Office Word e Microsoft Office Excel no nível de documento. Esses recursos bloqueiam usuários não autorizados de fazer alterações em partes protegidas de um documento.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Usando o Excel, você pode ativar a proteção e desativar enquanto a pasta de trabalho é aberta no designer. Usando o Word, você pode ativar a proteção somente fora do designer. Em tempo de execução, você pode habilitar ou desabilitar a proteção por meio de programação para Word e Excel.  
  
 Quando a proteção do documento é habilitada em um documento que está aberto no designer, todos os controles são retirados a **caixa de ferramentas** ou ficarão indisponíveis, e não é possível arrastar qualquer coisa, desde o **fontes de dados** janela para o documento.  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument e documentos protegidos  
 Se um documento estiver protegido, o cache de dados não pode ser acessado de fora do documento. Não é possível usar o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> de classe para recuperar ou manipular os dados armazenados em cache em um documento protegido, ou usar outros métodos do <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> classe.  
  
## <a name="word-document-protection-in-the-designer"></a>Proteção de documentos do Word no designer  
 Se você adicionar proteção a um documento do Word ou o modelo enquanto ele está aberto no Visual Studio, você não pode iniciar a aplicar a proteção no designer. O documento está no modo de design enquanto ele está aberto no Visual Studio, e ele deve estar no modo de execução antes de iniciar a imposição de proteção.  
  
 No entanto, se você criar um projeto que usa um documento do Word existente que tem proteção habilitada, o documento está protegido enquanto aberta no designer. Você não pode editar nas partes protegidas do documento, mas ainda é possível escrever código no Editor de códigos para automatizar o documento. Você também não é possível compilar o projeto se habilitar a proteção enquanto o documento está aberto no Visual Studio.  
  
 Você pode desativar proteção, enquanto o documento é aberto no designer para que você possa editar o documento e compilar o projeto. Você não pode desativar a proteção para a cópia no designer durante a depuração; o documento que é aberta durante a depuração é uma cópia separada do aberto no designer (a cópia de saída é armazenada na *\bin* diretório para o Visual Basic e o *\bin\debug* diretório para c#).  
  
 Você pode habilitar a proteção na cópia do documento que é aberta no designer de fechar o projeto no Visual Studio, abrindo a cópia do documento que está no diretório do projeto, e ativar a proteção.  
  
## <a name="enforce-word-document-protection-on-build"></a>Aplicar a proteção de documento do Word no build  
 Visual Studio inicia a imposição de proteção para documentos do Word e modelos durante o processo de compilação, para que a proteção é habilitada quando o documento é aberto para depuração. O documento é protegido com uma senha vazia.  
  
 A proteção é habilitado durante a compilação até que se houver código no documento <xref:Microsoft.Office.Tools.Word.Document.Startup> evento que pode causar exceções ou alterar o comportamento do aplicativo, esse código pode ser depurado corretamente. Se você habilitar a proteção depois que o documento for aberto, código de inicialização não pode ser depurado ou testado.  
  
## <a name="setting-the-password"></a>Configurar a senha  
 Visual Studio automaticamente habilita a proteção, mas não fornece nenhuma senha por padrão. Se você quiser que a proteção de documento para ter uma senha, você deve adicioná-lo antes de implantar sua solução. Adicionar uma senha permite que você permitir que os usuários autorizados a remover a proteção de documento; sem uma senha, proteção não pode ser removida facilmente. Para obter detalhes sobre como definir uma senha, consulte a Ajuda no aplicativo do Office específico.  
  
## <a name="see-also"></a>Consulte também  
 [Como: Proteger documentos e partes de documentos de forma programática](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Instruções passo a passo e exemplos de desenvolvimento do office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Gerenciamento de direitos de informação e visão geral das extensões de código gerenciado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Proteção por senha em documentos do Office](../vsto/password-protection-on-office-documents.md)   
 [Como: Permitir que o código execute documentos code-behind com permissões restritas](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)  
