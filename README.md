import graphene

class Query(graphene.ObjectType):
    hello = graphene.String(description='A typical hello world')

    def resolve_hello(self, info):
        return 'World'

schema = graphene.Schema(query=Query)
query = '''
    query SayHello {
      hello
    }
'''
result = schema.execute(query)
virtualenv venv
source venv/bin/activate
pip install -e ".[test]"
pytest graphene/relay/tests/test_node.py # Single file
pytest graphene/relay # All tests in directory
pytest graphene/relay/tests/test_node.py # Single file
pytest graphene/relay # All tests in directory
pre-commit install
pytest graphene --benchmark-only
tox
make docs

