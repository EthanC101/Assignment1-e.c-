package vcmsa.ci.assignment1ethanc


import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.TextView
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)

// User Interface (UI) from XML layout

        val txtMealPicker = findViewById<TextView>(R.id.txtMealPicker)
        val txtOptions = findViewById<TextView>(R.id.txtOptions)
        val edtTime = findViewById<EditText>(R.id.edtTime)
        val txtAnswer = findViewById<TextView>(R.id.txtAnswer)
        val btnSuggestion = findViewById<Button>(R.id.btnSuggestion)
        val btnReset = findViewById<Button>(R.id.btnReset)

// "Suggest Meal" button
        btnSuggestion.setOnClickListener {
            // Get the input from EditText and convert it to lowercase
            val time = edtTime.text.toString().trim().lowercase()


// if statements to determine the meal
            val suggestion = if (time == "morning") {
                "Breakfast: Smoothie"
            }
            else if (time == "mid-morning") {
                "Snack: Yoghurt"
            }
            else if (time == "afternoon") {
                "Lunch: A sandwich"
            }
            else if (time == "mid-afternoon") {
                "Snack: A piece of fruit"
            }
            else if (time == "dinner") {
                "Dinner: Steak,egg and chips"
            }
            else if (time == "after dinner") {
                "Dessert: Milkshake or popcorn"
            }
            else {
                "Invalid input. Please enter a valid time of day."
            }

            txtAnswer.text = suggestion

// Check if the input is blank and display an error message if it is
        if (time.isBlank()) {
            txtAnswer.text = "Please enter a time of day."
            return@setOnClickListener
        }
            // "Reset" button
            btnReset.setOnClickListener {
            // Clear the input
            edtTime.text.clear()
            txtAnswer.text = ""
        }
            ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main)) { v, insets ->
            val systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars())
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom)
            insets
             }
        }
    }
}
