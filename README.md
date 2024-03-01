from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/data', methods=['POST'])
def process_data():
    # Get the JSON data from the request
    data = request.json

    # Perform some processing on the data
    result = {}
    if 'name' in data and 'age' in data:
        result['status'] = 'success'
        result['message'] = 'Data processed successfully'
        result['name'] = data['name']
        result['age'] = data['age']
    else:
        result['status'] = 'error'
        result['message'] = 'Invalid data format'

    # Return the result as JSON response
    return jsonify(result)

if __name__ == '__main__':
    app.run(debug=True)
