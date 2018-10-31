# flask-wrapper-utilities
Handy wrapper utilities functions for Flask with SQLAlchemy.

# Usage Example
```python
from utils import jsonify_response, RouteError, paginate

PER_PAGE = 10
@some_router.route('URL')
@jsonify_response
@paginate
def get_some_list(pid):
    some_row = SomeModel.query.filter_by(id=pid).first()
    if not some_row:
        raise RouteError('Row does not exist.')
    page = flask.request.args.get('page', 1, type=int)
    pagination = SomeModel.paginate(page, 10, False)
    data = [your_row.some_method() for your_row in pagination.items]
    return pagination, data
```