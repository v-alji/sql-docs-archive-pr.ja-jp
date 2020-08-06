---
title: パッケージで注釈を使用する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- self-documenting packages
- adding annotations
- annotations [Integration Services]
ms.assetid: 48c8ed9a-b10d-490c-9ba7-4b77aa44e3dd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 27c7df6afd894ea9730027da1d54786ed8397fad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646209"
---
# <a name="use-annotations-in-packages"></a><span data-ttu-id="9fbea-102">パッケージで注釈を使用する</span><span class="sxs-lookup"><span data-stu-id="9fbea-102">Use Annotations in Packages</span></span>
  <span data-ttu-id="9fbea-103">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーには注釈の機能があります。注釈を使用すると、パッケージを自己文書化でき、パッケージを把握しやすくメンテナンスも容易になります。</span><span class="sxs-lookup"><span data-stu-id="9fbea-103">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer provides annotations, which you can use to make packages self-documenting and easier to understand and maintain.</span></span> <span data-ttu-id="9fbea-104">注釈は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーの、制御フロー、データ フロー、およびイベント ハンドラーのデザイン画面で追加できます。</span><span class="sxs-lookup"><span data-stu-id="9fbea-104">You can add annotations to the control flow, data flow, and event handler design surfaces of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="9fbea-105">注釈には任意のデータ型のテキストを含めることができるため、パッケージにラベル、コメント、その他の説明に関する情報を追加するのに便利です。</span><span class="sxs-lookup"><span data-stu-id="9fbea-105">The annotations can contain any type of text, and they are useful for adding labels, comments, and other descriptive information to a package.</span></span> <span data-ttu-id="9fbea-106">注釈は、デザイン時のみ機能します。</span><span class="sxs-lookup"><span data-stu-id="9fbea-106">Annotations are a design-time feature only.</span></span> <span data-ttu-id="9fbea-107">たとえば、注釈をログに書き込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="9fbea-107">For example, they are not written to logs.</span></span>  
  
 <span data-ttu-id="9fbea-108">Enter キーを押すと、テキストが次の行に折り返されます。</span><span class="sxs-lookup"><span data-stu-id="9fbea-108">When you press ENTER, the text wraps to the next line.</span></span> <span data-ttu-id="9fbea-109">テキスト行を追加すると、注釈ボックスのサイズが自動的に大きくなります。</span><span class="sxs-lookup"><span data-stu-id="9fbea-109">The annotation box automatically increases in size as you add additional lines of text.</span></span> <span data-ttu-id="9fbea-110">パッケージ ファイルの CDATA セクションでは、パッケージの注釈はクリア テキストで残ります。</span><span class="sxs-lookup"><span data-stu-id="9fbea-110">Package annotations are persisted as clear text in the CDATA section of the package file.</span></span>  
  
 <span data-ttu-id="9fbea-111">パッケージ ファイルの形式の変更の詳細については、「 [SSIS パッケージの形式](../../2014/integration-services/ssis-package-format.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9fbea-111">For more information about changes to the format of the package file, see [SSIS Package Format](../../2014/integration-services/ssis-package-format.md).</span></span>  
  
 <span data-ttu-id="9fbea-112">パッケージを保存すると、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーはパッケージ内に注釈を保存します。</span><span class="sxs-lookup"><span data-stu-id="9fbea-112">When you save the package, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer saves the annotations in the package.</span></span>  
  
### <a name="to-add-an-annotation-to-a-package"></a><span data-ttu-id="9fbea-113">パッケージに注釈を追加するには</span><span class="sxs-lookup"><span data-stu-id="9fbea-113">To add an annotation to a package</span></span>  
  
-   [<span data-ttu-id="9fbea-114">パッケージに注釈を追加する</span><span class="sxs-lookup"><span data-stu-id="9fbea-114">Add an Annotation to a Package</span></span>](../../2014/integration-services/add-an-annotation-to-a-package.md)  
  
  
