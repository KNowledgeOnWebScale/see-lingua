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

RDF as the web lingua.

Lingua supports reasoning with forward rules described in RDF as
```
:rulename lingua:premise _:premisename;
    lingua:conclusion _:conclusionname.

_:premisename {
    RDF triples
}

_:conclusionname {
    RDF triples
}
```

A forward rule with `lingua:conclusion` false is an inference fuse.

Lingua also supports reasoning with backward rules described in RDF as
```
:rulename lingua:headback _:headname;
    lingua:body _:bodyname.

_:headname {
    RDF triples
}

_:bodyname {
    RDF triples
}
```

Lingua also supports querying with queries described in RDF as
```
:queryname lingua:question _:questionname;
    lingua:answer _:answername.

_:questionname {
    RDF triples
}

_:answername {
    RDF triples
}
```

When `lingua:answer` is omitted it is the repetition of `lingua:question`.

The `lingua:` prefix is `<http://www.w3.org/2000/10/swap/lingua#>` and is rooted
in the "Semantic Web Area for Play" `http://www.w3.org/2000/10/swap/` URI.

The `var:` prefix is `<http://www.w3.org/2000/10/swap/var#>` and is used for
variables that are interpreted as universally quantified variables except for
forward rule conclusion-only variables which are interpreted existentially.

### Lingua also supports blogic https://www.slideshare.net/PatHayes/blogic-iswc-2009-invited-talk

The top level surface is an implicit positive surface with implicit graffiti.

`lingua:onPositiveSurface` is a positive surface.

`lingua:onNegativeSurface` is a negative surface used to express NAND based logic:
- nand (not and) is a `lingua:onNegativeSurface`
- negation is a `lingua:onNegativeSurface`
- disjunction is a `lingua:onNegativeSurface` containing only `lingua:onNegativeSurface`'s
- => is a `lingua:onNegativeSurface` containing a `lingua:onNegativeSurface`
- <= is a `lingua:onNegativeSurface` containing a `lingua:negativeTriple`

`lingua:onQuestionSurface` is a question surface containing an optional `lingua:onAnswerSurface`.

`lingua:onNeutralSurface` is a neutral surface.
