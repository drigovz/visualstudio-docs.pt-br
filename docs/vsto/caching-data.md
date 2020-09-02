---
title: Dados de cache
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c6e0f6d7fcf9920ddb8861712b7c5f8bf04506fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62939409"
---
# <a name="cache-data"></a>Dados de cache
  Você pode armazenar em cache objetos de dados em uma personalização em nível de documento para que os dados possam ser acessados offline ou sem abrir Microsoft Office Word ou Microsoft Office Excel. Para armazenar em cache um objeto, o objeto deve ter um tipo de dados que atenda a determinados requisitos. Muitos tipos de dados comuns no .NET Framework atendem a esses requisitos, incluindo <xref:System.String> , <xref:System.Data.DataSet> e <xref:System.Data.DataTable> .

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Há duas maneiras de adicionar um objeto ao cache de dados:

- Para adicionar um objeto ao cache de dados quando a solução é criada, aplique o <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo à declaração de objeto. Para obter mais informações, consulte [como armazenar em cache os dados para uso offline ou em um servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Para adicionar programaticamente um objeto ao cache de dados em tempo de execução, use o `StartCaching` método de um item de host, como as `ThisDocument` `ThisWorkbook` classes ou. Para obter mais informações, consulte [como: programaticamente armazenar em cache uma fonte de dados em um documento do Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

  Depois de adicionar um objeto ao cache de dados, você pode acessar e modificar os dados armazenados em cache sem iniciar o Word ou o Excel. Para obter mais informações, consulte [acessar dados em documentos no servidor](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="requirements-for-data-objects-to-be-cached"></a>Requisitos para objetos de dados a serem armazenados em cache
 Para armazenar em cache um objeto de dados em sua solução, o objeto deve atender a estes requisitos:

- Ser um campo público de leitura/gravação ou uma propriedade de um item de host, como as `ThisDocument` `ThisWorkbook` classes ou.

- Não ser um indexador ou outra propriedade com parâmetros.

  Além disso, o objeto de dados deve ser serializável pela <xref:System.Xml.Serialization.XmlSerializer> classe, o que significa que o tipo do objeto deve ter estas características:

- Ser um tipo público.

- Ter um construtor público sem parâmetros.

- Não execute código que exija privilégios de segurança adicionais.

- Expõe somente propriedades públicas de leitura/gravação (outras propriedades serão ignoradas).

- Não expor matrizes multidimensionais (matrizes aninhadas são aceitas).

- Não retornar interfaces de propriedades e campos.

- Não implementar <xref:System.Collections.IDictionary> se uma coleção.

  Quando você armazena em cache um objeto de dados, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializa o objeto em uma cadeia de caracteres XML que é armazenada em uma *parte XML personalizada* no documento. Para obter mais informações, consulte [visão geral de partes XML personalizadas](../vsto/custom-xml-parts-overview.md).

## <a name="cached-data-size-limits"></a>Limites de tamanho de dados em cache
 Há alguns limites para a quantidade total de dados que você pode adicionar ao cache de dados em um documento e ao tamanho de qualquer objeto individual no cache de dados. Se você exceder esses limites, o aplicativo poderá fechar inesperadamente quando os dados forem salvos no cache de dados.

 Para evitar esses limites, siga estas diretrizes:

- Não adicione nenhum objeto com mais de 10 MB ao cache de dados.

- Não adicione mais de 100 MB de dados totais ao cache de dados em um único documento.

  Esses são valores aproximados. Os limites exatos dependem de vários fatores, incluindo a RAM disponível e o número de processos em execução.

## <a name="control-the-behavior-of-cached-objects"></a>Controlar o comportamento de objetos em cache
 Para obter mais controle sobre o comportamento de um objeto armazenado em cache, você pode implementar a <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interface no tipo do objeto armazenado em cache. Por exemplo, você pode implementar essa interface se quiser controlar como o usuário é notificado quando o objeto tiver sido alterado. Para obter exemplos de código que demonstram como implementar <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> o, consulte a classe no exemplo de controles `ControlCollection` dinâmicos do Excel e no exemplo de controles dinâmicos do Word em [exemplos de desenvolvimento do Office e passo a passos](../vsto/office-development-samples-and-walkthroughs.md).

## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Manter alterações em dados armazenados em cache em documentos protegidos por senha
 Se você armazenar em cache objetos de dados em um documento protegido com uma senha, as alterações nos dados armazenados em cache não serão salvas. Você pode salvar as alterações nos dados armazenados em cache substituindo dois métodos. Substitua esses métodos para remover temporariamente a proteção quando o documento for salvo e reaplique a proteção após a conclusão da operação de salvamento.

 Para obter mais informações, consulte [como armazenar dados em cache em um documento protegido por senha](../vsto/how-to-cache-data-in-a-password-protected-document.md).

## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Evitar a perda de dados ao adicionar valores nulos ao cache de dados
 Quando você adiciona objetos ao cache de dados, todos os objetos armazenados em cache devem ser inicializados com um valor não**nulo** antes que o documento seja salvo e fechado. Se qualquer objeto armazenado em cache tiver um valor **nulo** quando o documento for salvo e fechado, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] removerá automaticamente todos os objetos armazenados em cache do cache de dados.

 Se você adicionar um objeto com um valor **nulo** ao cache de dados usando o <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo em tempo de design, poderá usar a <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe para inicializar os objetos de dados armazenados em cache antes de abrir o documento. Isso será útil se você quiser inicializar os dados armazenados em cache em um servidor sem o Word ou o Excel instalado, antes que o documento seja aberto por um usuário final. Para obter mais informações, consulte [acessar dados em documentos no servidor](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="see-also"></a>Confira também
- [Como armazenar em cache dados para uso offline ou em um servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Como: armazenar em cache uma fonte de dados programaticamente em um documento do Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Como armazenar dados em cache em um documento protegido por senha](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Walkthrough: criar uma relação de detalhes mestre usando um conjunto de um DataSet armazenado em cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)
