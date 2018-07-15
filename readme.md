**Integration tooling for annotation processors.**


A contract to be implemented by other annotation processors which - against the design philosophy of JSR 269 - alter
the types under compilation.

This contract will be queried by MapStruct when examining types referenced by mappers to be generated, most notably
the source and target types of mapping methods. If at least one AST-modifying processor announces further changes to
such type, the generation of the affected mapper(s) will be deferred to a future round in the annnotation processing
 cycle.

Implementations are discovered via the service loader, i.e. a JAR providing an AST-modifying processor needs to
declare its implementation in a file {@code META-INF/services/org.mapstruct.ap.spi.AstModifyingAnnotationProcessor}.
