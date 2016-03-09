---
layout: post
title: How to design API
tags: [api-design]
---
# [Oracle Java tutorials](https://docs.oracle.com/javase/tutorial/collections/interoperability/api-design.html)
- Parameters
  - Prefere interface over implementation
  - Always try to use the least-specific type that makes sense
- Return type
  - It is acceptable to use the more specific type as the return type. In fact, that should be the way to do it. For example, the method can return List instead of Collection so that the clients know for sure that the result collection is ordered and supports random access.

# [Regular API](https://dzone.com/articles/how-design-good-regular-api)
- Be consistent
  - On the terms
  - On argument order
- Be symmetric
  - On what you provide. e.g., if the API provides add(), then it should also provide remove()
  - On the terms
  - On the implementation
- Be convenient
  - On how the API is used

# [Effective API design](http://www.infoq.com/presentations/effective-api-design)

# [Checklist](http://theamiableapi.com/2012/01/16/java-api-design-checklist/)

# [Java API design guidelines](http://www.artima.com/weblogs/viewpost.jsp?thread=142428)
