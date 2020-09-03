---
title: Caixa de diálogo Configurar referência de serviço | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac8f4cf619bbdd007bb7aa570f549ae3c0b50e86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651109"
---
# <a name="configure-service-reference-dialog-box"></a>Caixa de diálogo Configurar Referência de Serviço
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A caixa de diálogo **Configurar referência de serviço** permite que você configure o comportamento dos [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] Serviços do.

> [!NOTE]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Para acessar a caixa de diálogo **Configurar referência de serviço** , clique com o botão direito do mouse em uma referência de serviço em **Gerenciador de soluções** e escolha **Configurar referência de serviço**. Você também pode acessar a caixa de diálogo clicando no botão **avançado** na **caixa de diálogo Adicionar referência de serviço**.

## <a name="task-list"></a>Lista de Tarefas

- Para alterar o endereço em que um serviço WCF está hospedado, insira o novo endereço no campo **endereço** .

- Para alterar o nível de acesso para classes em um cliente WCF, selecione uma palavra-chave de nível de acesso na lista **nível de acesso para classes geradas** .

- Para chamar os métodos de um serviço WCF de forma assíncrona, marque a caixa de seleção **gerar operações assíncronas** .

- Para gerar tipos de contrato de mensagem em um cliente WCF, marque a caixa de seleção **sempre gerar contratos de mensagem** .

- Para especificar os tipos de coleção de lista ou dicionário para um cliente WCF, selecione os tipos nas listas **tipo de coleção** e tipo de **coleção de dicionário** .

- Para desabilitar o compartilhamento de tipo, desmarque a caixa de seleção **reutilizar os tipos em assemblies referenciados** . Para habilitar o compartilhamento de tipo para um subconjunto de assemblies referenciados, marque a caixa de seleção **reutilizar os tipos em assemblies referenciados** , selecione **reutilizar os tipos em assemblies referenciados especificados**e selecione as referências desejadas na **lista assemblies referenciados**.

## <a name="uielement-list"></a>Lista de elementos de interface do usuário
 **Endereço** Usado para atualizar o endereço da Web em que uma referência de serviço procura um serviço. Por exemplo, durante o desenvolvimento, o serviço pode ser hospedado em um servidor de desenvolvimento, depois movido para um servidor de produção, precisando de uma alteração de endereço.

> [!NOTE]
> O elemento address não estará disponível quando a caixa de diálogo **Configurar referência de serviço** for exibida na **caixa de diálogo Adicionar referência de serviço**.

 **Nível de acesso para classes geradas** Determina o nível de acesso do código para classes de cliente WCF.

> [!NOTE]
> Para projetos de site, essa opção é sempre definida como `Public` e não pode ser alterada. Para obter mais informações, consulte [Solucionando problemas de referências de serviço](../data-tools/troubleshooting-service-references.md).

 **Gerar operações assíncronas** Determina se os métodos de serviço WCF serão chamados de forma síncrona (o padrão) ou assincronamente.

 **Gerar operações baseadas em tarefas** Ao escrever código assíncrono, essa opção permite que você aproveite a TPL (biblioteca paralela de tarefas) que foi introduzida com o .NET 4. Consulte a [TPL (biblioteca de paralelo de tarefas)](https://msdn.microsoft.com/library/dd460717.aspx).

 **Sempre gerar contratos de mensagem** Determina se os tipos de contrato de mensagem serão gerados para um cliente WCF. Para obter mais informações sobre os contratos de mensagem, consulte [usando contratos de mensagem](https://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249).

 **Tipo de coleção** Especifica o tipo de coleção de lista para um cliente WCF. O tipo padrão é <xref:System.Array>.

 **Tipo de coleção de dicionário** Especifica o tipo de coleção de dicionário para um cliente WCF. O tipo padrão é <xref:System.Collections.Generic.Dictionary%602>.

 **Reutilizar os tipos em assemblies referenciados** Determina se um cliente WCF tentará reutilizar o que já existe em assemblies referenciados em vez de gerar novos tipos quando um serviço for adicionado ou atualizado. Por padrão, essa opção está marcada.

 **Reutilizar os tipos em todos os assemblies referenciados** Quando selecionado, todos os tipos na **lista assemblies referenciados** serão reutilizados, se possível. Por padrão, essa opção é selecionada.

 **Reutilizar os tipos em assemblies referenciados especificados** Quando selecionado, somente os tipos selecionados na **lista assemblies referenciados** serão reutilizados.

 **Lista de assemblies referenciados** Contém uma lista de assemblies referenciados para o projeto ou site da Web. Quando a **reutilização de tipos em assemblies referenciados especificados** é selecionada, os assemblies individuais podem ser selecionados ou desmarcados.

 **Adicionar referência Web** Exibe a [caixa de diálogo NIB: Adicionar referência Web](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).

> [!NOTE]
> Essa opção deve ser usada somente para projetos direcionados à versão 2,0 do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

> [!NOTE]
> O botão **Adicionar referência Web** está disponível somente quando a caixa de diálogo **Configurar referência de serviço** é exibida na **caixa de diálogo Adicionar referência de serviço**.

## <a name="see-also"></a>Consulte Também
 [Como adicionar, atualizar ou remover uma referência de serviço](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9) [como: adicionar uma referência a um serviço Web](https://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168) [Windows Communication Foundation serviços e WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)
