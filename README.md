```{=org}
#+cite_export:
```
# Security features

  Name                                                                    Description
  ----------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [Cyber Deception](https://github.com/fluidos-project/cyber-deception)   The Cyber Deception feature, part of the FLUIDOS Cyber Security services designed to improve the overall security of the ecosystem, is willing to provide Cloud Native Cyber Deception as a Service (CDaaS) integrated into the FLUIDOS continuum.

# Security features integration

## Type of features

We identified fours type of security features and their respective
integration strategy:

Integrated by design

:   -   What does it do?
    -   How is it advertised?
    -   How is it used?

Service

:   -   What does it do?
    -   How is it advertised?
    -   How is it used?

Without Contoller

:   -   What does it do?
    -   How is it advertised?
    -   How is it used?

With Controller

:   -   What does it do?
    -   How is it advertised?
    -   How is it used?

## How-To create a Testbed

In order for every partner to test the implementation of each security
feature a FLUIDOS testbed should be created. Here are pointers to the
documentation for creating a testbed:

1.  [FLUIDOS Node testbed
    installation](https://github.com/fluidos-project/node/blob/main/docs/installation/installation.md)
2.  [FLUIDOS Model-based Meta-Orchestrator testbed
    installation](https://github.com/fluidos-project/fluidos-modelbased-metaorchestrator/tree/main/utils/testbed)

## Integrate a feature of type \"Service\"

## [TODO]{.todo .TODO} Integrate a feature of type \"Without controller\" {#integrate-a-feature-of-type-without-controller}

As capabilities: `aditionalProperties`{.verbatim} in the FLAVOR (eg:
MAGI and TEE):

1.  Every node has a FLAVOR CRD
2.  For every service we should define the Intent template:
    [example1](https://github.com/fluidos-project/fluidos-modelbased-metaorchestrator/blob/main/utils/examples/carbon-intent.yaml),
    [example2](https://github.com/fluidos-project/fluidos-modelbased-metaorchestrator/blob/demo-Y2-stable/utils/testbed/intent-demo.yaml)
3.  For every service we should provide the python code for validation
    by modifying in this
    [file](https://github.com/fluidos-project/fluidos-modelbased-metaorchestrator/blob/demo-Y2-stable/fluidos_model_orchestrator/common.py):
    1.  `KnownIntent`{.verbatim} function: the function that advertise
        the Intent (just enumerating them with its own validation
        function)
    2.  `validate_*`{.verbatim} function: the function that validate the
        Intent wrt the added parameters, eg:
        `validate_location`{.verbatim}
4.  Modifications on step 3) must be added in the code of the
    meta-orchestrator via a dedicated PR
5.  On every node instance providing such security feature (eg: on your
    testbed) we need to patch the FLAVOR CRD with the relevant
    additional properties:
    [example](https://github.com/fluidos-project/fluidos-modelbased-metaorchestrator/blob/main/tests/examples/bandwidth-patch-file.yaml)
6.  This sort of [unit
    test](https://github.com/fluidos-project/fluidos-modelbased-metaorchestrator/blob/main/tests/test_intent_satisfaction.py)
    should help to verify everything is ok regarding your Intent
7.  Content of this
    [folder](https://github.com/fluidos-project/fluidos-modelbased-metaorchestrator/tree/demo-Y2-stable/tests)
    may also be useful
8.  The last step is to verify an end-to-end test using the
    meta-orchestrator, which could be launched locally with
    `Kops`{.verbatim}

## [TODO]{.todo .TODO} Integrate a feature of type \"With controller\" {#integrate-a-feature-of-type-with-controller}

As capabilities with own controller (via dedicated FLAVOR and Service
category, when there is a controller and a CRD) (eg: Decepto and FLAD)

1.  Slides
    [here](https://docs.google.com/presentation/d/1C3aC8YEbpfUUjlVeytbBNp9-22bTe4mI/edit#slide=id.p1)
2.  FLUIDOS node \> v0.1.0 supports FLAVORS
3.  Service categories are needed when we need to deploy a CRD on the
    provider cluster
4.  Service flavor: sw owner, deployed and managed by the provider
    cluster
5.  Two categories (db and XXX) are supported by the FLUIDOS node,
    definition of a service category requires modification of FLUIDOS
    node
6.  RBAC are quite open now, in order to support creation of many
    resources
7.  Specific RBAC are required to create CRD
8.  Other interesting references:
    -   <https://github.com/fluidos-project/fluidos-ontology>
    -   <https://github.com/fluidos-project/REAR-data-models>
    -   <https://github.com/fluidos-project/REAR/blob/main/docs/messages/README.md#get-the-list-of-available-flavors>
    -   <https://github.com/fluidos-project/REAR-data-models/blob/master/models/schemas/flavor.schema.json>

# Demos
