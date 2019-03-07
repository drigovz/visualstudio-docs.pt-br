---
title: Considerações de segurança para trabalhar com dados XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3af91f02b6cc34fcc05b83bb6c09cfd37e8a18ef
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525460"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Considerações de segurança ao trabalhar com dados XML

Este tópico discute problemas de segurança que você precisa saber sobre ao trabalhar com o editor XML ou o depurador XSLT.

## <a name="xml-editor"></a>Editor de XML

 O editor de XML é baseado no Editor de texto do Visual Studio. Depende de classes de <xref:System.Xml> e de <xref:System.Xml.Xsl> para manipular muitos dos processos XML.

-   As transformações XSLT são executadas em um domínio de aplicativo. As transformações XSLT *área restrita e*; ou seja, a política de segurança de acesso do código do seu computador é usada para determinar as permissões restritas com base em onde se encontra a folha de estilos XSLT. Por exemplo, folhas de estilos de um local da Internet tem as permissões as mais rígidas, enquanto as folhas de estilos copiaram ao seu disco rígido executado com confiança total.

-   A classe de <xref:System.Xml.Xsl.XslCompiledTransform> é usado para compilar XSLT a Microsoft intermediate language para aumentar o desempenho durante a execução.

-   Os esquemas apontando para um local externo no arquivo de catálogo são baixados automaticamente quando o editor de XML é carregado pela primeira vez. A classe de <xref:System.Xml.Schema.XmlSchemaSet> é usada para criar esquemas. O arquivo de catálogo que é fornecido com o editor de XML não tem links para todos os esquemas externos. O usuário deve adicionar explicitamente uma referência para o esquema externa antes que o editor XML baixar o arquivo de esquema. Baixar HTTP pode ser desabilitado por meio de **diversas opções de ferramentas** página para o editor de XML.

-   O editor XML usa o <xref:System.Net> classes para baixar esquemas

## <a name="xslt-debugger"></a>Depurador XSLT

 O depurador XSLT usa o mecanismo e as classes gerenciadas Visual Studio de depuração de <xref:System.Xml> e do espaço de <xref:System.Xml.Xsl> .

-   O depurador XSLT executa cada transformação XSLT em um domínio de aplicativo na área restrita. A política de segurança de acesso a código do seu computador é usada para determinar as permissões restritas com base em onde a folha de estilos XSLT é encontrada. Por exemplo, folhas de estilos de um local da Internet tem as permissões as mais rígidas, enquanto as folhas de estilos copiaram ao seu disco rígido executado com confiança total.

-   A folha de estilos XSLT é compilada usando a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .

-   O avaliador de expressão XSLT é carregado pelo mecanismo gerenciado de depuração. O mecanismo gerenciado de depuração supõe que qualquer código é executado do computador local do usuário. Da mesma forma, a classe de <xref:System.Xml.Xsl.XslCompiledTransform> download do arquivo fonte para o computador local do usuário. A possibilidade que um ataue de elevação de privilégio em execução pode ocorrer é abrandada executando todas as transformações XSLT em um domínio de aplicativo com permissões restritas

## <a name="see-also"></a>Consulte também

- [Domínios do aplicativo](/dotnet/framework/app-domains/application-domains)