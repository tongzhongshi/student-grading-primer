# Document your edge case here
- To get marks for this section you will need to explain to your tutor:
1) The edge case identified:
The edge case I identified is requesting the /stats endpoint when the student database is empty (contains no records).

2) How I accounted for this in my implementation:
I implemented a conditional check at the beginning of the get_stats function in backend/app.py.

Detection: The code first retrieves the list of students using db.get_all_students().

Handling: If the list is empty, the function immediately returns a JSON response with all statistical fields (count, average, min, max) set to 0, along with a 200 OK status code.
    stats = {
        "count": len(students),
        "average": sum(marks) / len(marks) if marks else 0,
        "min": min(marks) if marks else 0,
        "max": max(marks) if marks else 0
    }
    return jsonify(stats), 200