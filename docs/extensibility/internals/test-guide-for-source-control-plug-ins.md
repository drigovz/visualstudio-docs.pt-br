---
title: Guia de teste para Plug-ins de controle do código-fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0bf16f79401f4b8df3bafff0f92963510110dff1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56622755"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guia de teste para plug-ins de controle do código-fonte
Esta seção fornece diretrizes para testar o plug-in com o controle de origem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. É fornecida uma visão geral abrangente das áreas mais comuns de testes, bem como algumas das áreas mais complexas que podem ser um problemas. Esta visão geral não deve ser uma lista completa de casos de teste.

> [!NOTE]
>  Algumas correções de bugs e melhorias para a versão mais recente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE pode revelar problemas com existente fonte plug-ins de controle que anteriormente não foram encontrados durante o uso de versões anteriores do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. É altamente recomendável que você teste seu controle de origem existente plug-in para as áreas enumeradas nesta seção, mesmo que nenhuma alteração foi feita para o plug-in desde a versão anterior do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="common-preparation"></a>Preparação comuns
 Uma máquina com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e o plug-in de controle do código-fonte de destino instalado, é necessário. Uma segunda máquina configurada da mesma forma pode ser usada para algumas da abrir do controle de origem de testes.

## <a name="definition-of-terms"></a>Definição de termos
 Com a finalidade deste guia de teste, use as seguintes definições de termos:

 Cliente de qualquer tipo de projeto disponível no projeto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que dá suporte à integração de controle do código-fonte (por exemplo, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], ou [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).

 Projeto da Web são os quatro tipos de projetos da Web: Sistema de arquivos, IIS Local, Sites remotos e FTP.

- Projetos do sistema de arquivos são criados em um caminho local, mas eles não exigem o Internet Information Services (IIS) a serem instalados conforme elas são acessadas internamente por meio de um caminho UNC e podem ser colocadas sob controle de origem de dentro do IDE, assim como projetos de cliente.

- Projetos do IIS locais funcionam com o IIS está instalado no mesmo computador e é acessado com uma URL que aponta para o computador local.

- Projetos de Sites remotos também são criados em um serviços do IIS, mas eles são colocados sob controle do código-fonte no computador do servidor do IIS e não de dentro do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- Projetos FTP são acessados por meio de um servidor FTP remoto, mas eles não podem ser colocados sob controle do código-fonte.

  A inscrição do controle de outro termo para a solução ou projeto em código-fonte.

  Versão Store do banco de dados de controle de origem que está sendo acessado por meio da API de plug-in de controle de origem.

## <a name="test-areas-covered-in-this-section"></a>Áreas de teste abordadas nesta seção

-   [Área de teste 1: Adicionar ao / abrir do controle de origem](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

    -   Caso 1a: Adicionar solução ao controle do código-fonte

    -   Caso 1b: Abrir solução do controle de origem

    -   Caso 1c: Adicionar solução de controle de origem

-   [Área de teste 2: Obter do controle de origem](../../extensibility/internals/test-area-2-get-from-source-control.md)

-   [Área de teste 3: Check Out/Undo Checkout](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

    -   Caso 3: Fazer Check-Out / desfazer check-out

    -   Caso 3a: Fazer Check-Out

    -   Caso 3b: Check-out desconectado

    -   Caso 3c: Editar consulta/consulta salvar (QEQS)

    -   3d de caso: Check-out silenciosa

    -   Caso 3e: Desfazer check-out

-   [Área de teste 4: Fazer Check-in](../../extensibility/internals/test-area-4-check-in.md)

    -   Caso 4a: Itens modificados

    -   Caso 4b: Adicionando arquivos

    -   Caso 4c: Adicionando projetos

-   [Área de teste 5: Alterar controle do código-fonte](../../extensibility/internals/test-area-5-change-source-control.md)

    -   Caso 5a: associar

    -   Caso 5b: desassociar

    -   Caso 5c: Reassociar

-   [Área de teste 6: Delete](../../extensibility/internals/test-area-6-delete.md)

-   [Área de teste 7: Compartilhar](../../extensibility/internals/test-area-7-share.md)

-   [Área de teste 8: Alternância de plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)

    -   8a case: Alterações automáticas

    -   8b case: Alteração de solução

## <a name="see-also"></a>Consulte também
- [Plug-ins de controle do código-fonte](../../extensibility/source-control-plug-ins.md)