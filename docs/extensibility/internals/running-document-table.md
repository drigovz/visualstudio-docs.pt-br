---
title: Executando tabela de documentos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4645899e8c4cd73758316a3c2a8d74ccb169aa2d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724064"
---
# <a name="running-document-table"></a>Tabela de documento em execução
O IDE mantém a lista de todos os documentos abertos no momento em uma estrutura interna chamada RDT (tabela de documentos em execução). Essa lista inclui todos os documentos abertos na memória, independentemente se esses documentos estão sendo editados no momento. Um documento é qualquer item persistido, incluindo arquivos em um projeto ou no arquivo de projeto principal (por exemplo, um arquivo. vcxproj).

## <a name="elements-of-the-running-document-table"></a>Elementos da tabela de documentos em execução
 A tabela documento em execução contém as entradas a seguir.

|Elemento|Descrição|
|-------------|-----------------|
|Moniker do documento|Uma cadeia de caracteres que identifica exclusivamente o objeto de dados do documento. Esse seria o caminho de arquivo absoluto para um sistema de projeto que gerencia arquivos (por exemplo, C:\MyProject\MyFile). Essa cadeia de caracteres também é usada para projetos salvos em repositórios diferentes de sistemas de arquivos, como procedimentos armazenados em um banco de dados. Nesse caso, o sistema de projeto pode inventar uma cadeia de caracteres exclusiva que pode ser reconhecida e possivelmente analisada para determinar como armazenar o documento.|
|Proprietário da hierarquia|O objeto de hierarquia que possui o documento, conforme representado por uma interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.|
|ID do item|Identificador de item para um item específico dentro da hierarquia. Esse valor é exclusivo entre todos os documentos na hierarquia que possui este documento, mas esse valor não tem garantia de ser exclusivo entre hierarquias diferentes.|
|Objeto de dados do documento|No mínimo, isso é um `IUnknown`<br /><br /> . O IDE não requer nenhuma interface específica além da interface `IUnknown` para o objeto de dados de documento de um editor personalizado. No entanto, para um editor padrão, a implementação do editor da interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> é necessária para lidar com chamadas de persistência de arquivo do projeto. Para obter mais informações, consulte [salvando um documento padrão](../../extensibility/internals/saving-a-standard-document.md).|
|Sinalizadores|Sinalizadores que controlam se o documento é salvo, se um bloqueio de leitura ou de edição é aplicado e assim por diante, pode ser especificado quando as entradas são adicionadas ao RDT. Para obter mais informações, consulte a enumeração <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|
|Editar contagem de bloqueios|Contagem de bloqueios de edição. Um bloqueio de edição indica que algum editor tem o documento aberto para edição. Quando a contagem de bloqueios de edição faz a transição para zero, o usuário é solicitado a salvar o documento, se ele tiver sido modificado. Por exemplo, toda vez que você abre um documento em um editor usando o comando **nova janela** , um bloqueio de edição é adicionado ao documento no RDT. Para que um bloqueio de edição seja definido, o documento deve ter uma hierarquia ou ID de item.|
|Contagem de bloqueios de leitura|Contagem de bloqueios de leitura. Um bloqueio de leitura indica que o documento está sendo lido por meio de algum mecanismo, como um assistente. Um bloqueio de leitura mantém um documento ativo no RDT enquanto indica que o documento não pode ser editado. Você pode definir um bloqueio de leitura mesmo que o documento não tenha uma ID de item ou de hierarquia. Esse recurso permite abrir um documento na memória e inseri-lo no RDT sem que o documento seja de propriedade de qualquer hierarquia. Esse recurso é raramente usado.|
|Proprietário do bloqueio|Uma instância de uma interface de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>. O proprietário do bloqueio é implementado por recursos como assistentes que abrem e editam documentos fora de um editor. Um proprietário de bloqueio permite que o recurso adicione um bloqueio de edição ao documento para impedir que o documento seja fechado enquanto ainda está sendo editado. Normalmente, os bloqueios de edição são adicionados apenas por janelas de documentos (ou seja, editores).|

 Cada entrada no RDT tem uma hierarquia exclusiva ou ID de item associada a ela, que geralmente corresponde a um nó no projeto. Todos os documentos disponíveis para edição normalmente são de propriedade de uma hierarquia. As entradas feitas no RDT controlam qual projeto, ou — mais precisamente — qual hierarquia, atualmente é proprietária do objeto de dados de documento que está sendo editado. Usando as informações no RDT, o IDE pode impedir que um documento seja aberto por mais de um projeto por vez.

 A hierarquia também controla a persistência de dados e usa as informações no RDT para atualizar as caixas de diálogo **salvar** e **salvar como** . Quando os usuários modificam um documento e escolhem o comando **sair** no menu **arquivo** , o IDE os solicita com a caixa de diálogo **salvar alterações** para mostrar todos os projetos e itens de projeto que estão atualmente modificados. Isso permite que os usuários escolham quais documentos salvar. A lista de documentos a serem salvos (ou seja, os documentos que têm alterações) é gerada por meio do RDT. Todos os itens que você espera ver na caixa de diálogo **salvar alterações** após sair do aplicativo devem ter registros no RDT. O RDT coordena quais documentos são salvos e se o usuário é avisado sobre uma operação de salvamento usando os valores especificados na entrada de sinalizadores para cada documento. Para obter mais informações sobre os sinalizadores RDT, consulte a enumeração <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.

## <a name="edit-locks-and-read-locks"></a>Editar bloqueios e ler bloqueios
 Editar bloqueios e bloqueios de leitura residem no RDT. A janela do documento incrementa e decrementa o bloqueio de edição. Assim, quando um usuário abre uma nova janela de documento, a contagem de bloqueios de edição é incrementada em um. Quando o número de bloqueios de edição chega a zero, a hierarquia é sinalizada para persistir ou salvar os dados do documento associado. A hierarquia pode persistir os dados de qualquer forma, incluindo a persistência como um arquivo ou como um item em um repositório. Você pode usar o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> na interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> para adicionar os bloqueios de edição e de leitura e o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> para remover esses bloqueios.

 Normalmente, quando a janela do documento de um editor é instanciada, o quadro da janela adiciona automaticamente um bloqueio de edição para o documento no RDT. No entanto, se você criar uma exibição personalizada de um documento que não usa uma janela de documento padrão (ou seja, ela não implementa a interface de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>), você precisará definir seu próprio bloqueio de edição. Por exemplo, em um assistente, um documento é editado sem ser aberto em um editor. Para que os bloqueios de documentos sejam abertos por assistentes e entidades semelhantes, essas entidades devem implementar a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>. Para registrar o proprietário do bloqueio de documento, chame o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> e passe sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>. Isso adiciona o proprietário do bloqueio de documento ao RDT. Outro cenário para implementar um detentor de bloqueio de documento é se você abrir um documento por meio de uma janela de ferramenta especial. Nessa instância, você não pode fazer com que a janela de ferramentas feche o documento. No entanto, ao se registrar como um detentor de bloqueio de documento no RDT, o IDE pode chamar a implementação do método <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> para solicitar um fechamento do documento.

## <a name="other-uses-of-the-running-document-table"></a>Outros usos da tabela de documentos em execução
 Outras entidades no IDE usam o RDT para obter informações sobre documentos. Por exemplo, o Gerenciador de controle do código-fonte usa o RDT para instruir o sistema a recarregar um documento no editor, depois de obter a versão mais recente do arquivo. Para fazer isso, o Gerenciador de controle do código-fonte pesquisa os arquivos no RDT para ver se algum deles está aberto. Se estiverem, o Gerenciador de controle do código-fonte primeiro verificará se a hierarquia implementa o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>. Se o projeto não implementar o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>, o Gerenciador de controle do código-fonte verificará se há uma implementação do método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> no objeto de dados do documento diretamente.

 O IDE também usa o RDT para resuperfície (trazer para a frente) um documento aberto, se um usuário solicitar esse documento. Para obter mais informações, consulte [exibindo arquivos usando o comando abrir arquivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Para determinar se um arquivo está aberto no RDT, siga um destes procedimentos.

- Consulte o moniker do documento (ou seja, o caminho completo do documento) para descobrir se o item está aberto.

- Use a hierarquia ou a ID do item para pedir ao sistema do projeto o caminho completo do documento e, em seguida, procure o item no RDT.

## <a name="see-also"></a>Consulte também
- [Uso de RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Persistência e tabela de documento em execução](../../extensibility/internals/persistence-and-the-running-document-table.md)