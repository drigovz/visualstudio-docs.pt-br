---
title: Elemento Bitmap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d663351aad7d381dd5bfe4cbaa0a263cc70b821
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740002"
---
# <a name="bitmap-element"></a>Elemento Bitmap
Define um bitmap. O bitmap é carregado a partir de um recurso ou de um arquivo.

## <a name="syntax"></a>Sintaxe

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|guid|Obrigatórios. GUIA do identificador de comando GUID/ID.<br /><br /> O atributo guid para um bitmap não está associado a nenhum VSPackage ou outro grupo de comando.  Ele deve ser exclusivo da definição bitmap e não deve ser usado para qualquer outro propósito.|
|Resid|ID do identificador de comando GUID/ID. Ou o resID ou o atributo href são necessários.<br /><br /> O atributo resID é um ID de recurso inteiro que determina a tira de bitmap que deve ser carregada durante a fusão da tabela de comando.  Quando a tabela de comando estiver sendo carregada, os bitmaps especificados pelo ID de recurso serão carregados a partir do recurso do mesmo módulo.|
|usedList|Necessário se o atributo resID estiver presente. Seleciona as imagens disponíveis na tira bitmap.|
|href|Caminho para o bitmap. Ou o resID ou o atributo href são necessários.<br /><br /> O caminho de inclusão é pesquisado para o arquivo de imagem indicado, que está incorporado no binário resultante.  Durante a fusão da tabela de comando, a imagem é copiada e não é necessária pesquisa ou carga adicional de recursos.  Se o atributo usedList não estiver presente, todas as imagens da tira estão disponíveis. **Nota:**  As imagens podem ser fornecidas em um dos vários formatos que incluem *.bmp*, *.png*e *.gif*.  As versões anteriores do compilador não suportam imagens de bitmap de 32 bits que tinham informações alfa para transparência parcial. A solução para essas versões é usar o formato *.png.*|
|Condição|Opcional. Ver [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos filho
 Nenhum.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento Bitmaps](../extensibility/bitmaps-element.md)|Grupos elementos do Bitmap.|

## <a name="example"></a>Exemplo

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Confira também
- [Arquivos da tabela de comando do Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
