# Second Eye of Euler - SEE

Reasoning engine that is talking RDF TriG as the web lingua.

Examples are in [lingua](https://github.com/eyereasoner/see-lingua/tree/main/lingua) and their output in [lingua/output](https://github.com/eyereasoner/see-lingua/tree/main/lingua/output)

```
Usage: see <options>* <data>*

<options>
    --genid <genid>             use <genid> in Skolem IRIs
    --help                      show help info
    --output <file>             write reasoner output to <file>
    --version                   show version info
    --wcache <uri> <file>       to tell that <uri> is cached as <file>

<data>
    <uri>                       TriG data
```

## RDF Lingua

RDF TriG as the web lingua.

Lingua supports reasoning with forward rules described in RDF as
```
_:ng1 lingua:implication _:ng2.

_:ng1 {
    RDF triples
}

_:ng2 {
    RDF triples
}
```

A forward rule with `lingua:implication false` is an inference fuse.

Lingua also supports reasoning with backward rules described in RDF as
```
_:ng1 lingua:if _:ng2.

_:ng1 {
    RDF triples
}

_:ng2 {
    RDF triples
}
```

Lingua also supports querying with queries described in RDF as
```
_:ng1 lingua:query _:ng2.

_:ng1 {
    RDF triples
}

_:ng2 {
    RDF triples
}
```

The `lingua:` prefix is `<http://www.w3.org/2000/10/swap/lingua#>` and is rooted
in the "Semantic Web Area for Play" `http://www.w3.org/2000/10/swap/` URI.

The `var:` prefix is `<http://www.w3.org/2000/10/swap/var#>` and is used for
variables that are interpreted as universally quantified variables except for
forward rule conclusion-only variables which are interpreted existentially.

## RDF Lingua Surfaces

See https://www.slideshare.net/PatHayes/blogic-iswc-2009-invited-talk

The top level surface is an implicit positive surface with implicit graffiti.

`lingua:nand` is a negative surface used to express NAND based logic:
- nand (not and) is a `lingua:nand`
- negation is a `lingua:nand`
- disjunction is a `lingua:nand` containing only `lingua:nand`'s
- implication is a `lingua:nand` containing a `lingua:nand`
