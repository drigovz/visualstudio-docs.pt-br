---
title: Tabela de documentos em execução | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e6aa882921786b1592922372581beae8c4c2443
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705561"
---
# <a name="running-document-table"></a>Tabela de documento em execução
O IDE mantém a lista de todos os documentos atualmente abertos em uma estrutura interna chamada rdt (corrente de documentos em execução). Esta lista inclui todos os documentos abertos na memória, independentemente de esses documentos estarem sendo editados no momento. Um documento é qualquer item que persiste, incluindo arquivos em um projeto ou no arquivo principal do projeto (por exemplo, um arquivo .vcxproj).

## <a name="elements-of-the-running-document-table"></a>Elementos da tabela de documentos em execução
 A tabela de documentos em execução contém as seguintes entradas.

|Elemento|Descrição|
|-------------|-----------------|
|Apelido de documento|Uma seqüência que identifica exclusivamente o objeto de dados do documento. Este seria o caminho de arquivo absoluto para um sistema de projeto que gerencia arquivos (por exemplo, C:\MyProject\MyFile). Essa string também é usada para projetos salvos em lojas diferentes de sistemas de arquivos, como procedimentos armazenados em um banco de dados. Neste caso, o sistema de projeto pode inventar uma seqüência única que ele pode reconhecer e possivelmente analisar para determinar como armazenar o documento.|
|Proprietário de hierarquia|O objeto de hierarquia que possui o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> documento, representado por uma interface.|
|Item ID|Identificador de item para um item específico dentro da hierarquia. Esse valor é único entre todos os documentos da hierarquia que possui este documento, mas esse valor não é garantido para ser único em diferentes hierarquias.|
|Objeto de dados de documento|No mínimo, este é um`IUnknown`<br /><br /> . O IDE não requer nenhuma `IUnknown` interface específica além da interface para o objeto de dados de documento de um editor personalizado. No entanto, para um editor padrão, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> a implementação da interface pelo editor é necessária para lidar com chamadas de persistência de arquivos do projeto. Para obter mais informações, consulte [Salvando um documento padrão](../../extensibility/internals/saving-a-standard-document.md).|
|Flags|Sinalizadores que controlam se o documento está salvo, se um bloqueio de leitura ou edição é aplicado e assim por diante, podem ser especificados quando as entradas são adicionadas ao RDT. Para obter mais informações, consulte a enumeração <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|
|Editar contagem de bloqueio|Contagem de bloqueios de edição. Um bloqueio de edição indica que algum editor tem o documento aberto para edição. Quando a contagem de bloqueios de edição passa para zero, o usuário é solicitado a salvar o documento, se ele tiver sido modificado. Por exemplo, toda vez que você abre um documento em um editor usando o comando **Nova janela,** um bloqueio de edição é adicionado para esse documento no RDT. Para que um bloqueio de edição seja definido, o documento deve ter uma hierarquia ou id do item.|
|Ler contagem de bloqueio|Contagem de fechaduras de leitura. Um bloqueio de leitura indica que o documento está sendo lido através de algum mecanismo, como um assistente. Um bloqueio de leitura mantém um documento vivo no RDT, indicando que o documento não pode ser editado. Você pode definir um bloqueio de leitura mesmo que o documento não tenha uma hierarquia ou id de item. Esse recurso permite que você abra um documento na memória e insira-o no RDT sem que o documento seja de propriedade de qualquer hierarquia. Este recurso raramente é usado.|
|Suporte de bloqueio|Um exemplo <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> de interface. O suporte de bloqueio é implementado por recursos como assistentes que abrem e editam documentos fora de um editor. Um suporte de bloqueio permite que o recurso adicione um bloqueio de edição ao documento para evitar que o documento seja fechado enquanto ele ainda está sendo editado. Normalmente, os bloqueios de edição só são adicionados por janelas de documentos (ou seja, editores).|

 Cada entrada no RDT tem uma hierarquia ou ID de item único associado a ele, que geralmente corresponde a um nó no projeto. Todos os documentos disponíveis para edição são tipicamente de propriedade de uma hierarquia. Entradas feitas no controle RDT que projetam, ou — com mais precisão — qual hierarquia atualmente possui o objeto de dados do documento que está sendo editado. Usando as informações no RDT, o IDE pode impedir que um documento seja aberto por mais de um projeto por vez.

 A hierarquia também controla a persistência dos dados e usa as informações no RDT para atualizar as caixas de diálogo **Salvar** e **Salvar como.** Quando os usuários modificam um documento e escolhem o comando **Sair** no menu **Arquivo,** o IDE solicita-os com a caixa de diálogo **Salvar alterações** para mostrar a todos os projetos e itens do projeto que estão atualmente modificados. Isso permite que os usuários escolham qual dos documentos salvar. A lista de documentos a serem saqueados (ou seja, aqueles documentos que têm alterações) é gerada a partir do RDT. Todos os itens que você espera ver na caixa de diálogo **Salvar alterações** ao sair do aplicativo devem ter registros no RDT. O RDT coordena quais documentos são salvos e se o usuário é solicitado sobre uma operação de salvamento usando os valores especificados na entrada Sinalizadores para cada documento. Para obter mais informações sobre as <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> bandeiras RDT, consulte a enumeração.

## <a name="edit-locks-and-read-locks"></a>Editar bloqueios e bloqueios de leitura
 Editar bloqueios e ler bloqueios residem no RDT. A janela do documento aumenta e decreta o bloqueio de edição. Assim, quando um usuário abre uma nova janela de documento, a contagem de bloqueio de edição aumenta por um. Quando o número de bloqueios de edição atinge zero, a hierarquia é sinalizada para persistir ou salvar os dados para o documento associado. A hierarquia pode então persistir os dados de qualquer forma, incluindo persistir como um arquivo ou como um item em um repositório. Você pode <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> método na interface para adicionar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> bloqueios de edição e bloqueios de leitura, e o método para remover essas fechaduras.

 Normalmente, quando a janela do documento para um editor é instanciada, o quadro da janela adiciona automaticamente um bloqueio de edição para o documento no RDT. No entanto, se você criar uma exibição personalizada de um documento que não <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> usa uma janela de documento padrão (ou seja, ela não implementa a interface), então você precisa definir seu próprio bloqueio de edição. Por exemplo, em um assistente, um documento é editado sem ser aberto em um editor. Para que os bloqueios de documentos sejam abertos por assistentes e <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> entidades semelhantes, essas entidades devem implementar a interface. Para registrar o suporte de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> bloqueio do documento, ligue para o método e passe na sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementação. Ao fazer isso, adiciona o suporte de bloqueio do documento ao RDT. Outro cenário para implementar um suporte de bloqueio de documento é se você abrir um documento através de uma janela de ferramenta especial. Neste caso, você não pode fazer com que a janela da ferramenta feche o documento. No entanto, ao registrar-se como um titular de bloqueio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> documento no RDT, o IDE pode chamar sua implementação do método para solicitar o fechamento do documento.

## <a name="other-uses-of-the-running-document-table"></a>Outros usos da tabela de documentos em execução
 Outras entidades do IDE utilizam o RDT para obter informações sobre documentos. Por exemplo, o gerenciador de controle de origem usa o RDT para dizer ao sistema para recarregar um documento no editor, depois que ele obtém a versão mais recente do arquivo. Para fazer isso, o gerenciador de controle de origem procura os arquivos no RDT para ver se algum deles está aberto. Se forem, o gerenciador de controle de origem verifica <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> primeiro para ver se a hierarquia implementa o método. Se o projeto não <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementar o método, o gerenciador <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> de controle de origem verifica diretamente a implementação do método no objeto de dados do documento.

 O IDE também usa o RDT para ressurgir (trazer para a frente) um documento aberto, caso um usuário solicite esse documento. Para obter mais informações, consulte [Exibindo arquivos usando o comando Open File .](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md) Para determinar se um arquivo está aberto no RDT, faça um o seguinte.

- Consulte o nome do documento (ou seja, o caminho completo do documento) para saber se o item está aberto.

- Use a hierarquia ou id do item para pedir ao sistema de projeto o caminho completo do documento e, em seguida, procure o item no RDT.

## <a name="see-also"></a>Confira também
- [Uso de RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Persistência e a tabela de documentos em execução](../../extensibility/internals/persistence-and-the-running-document-table.md)
